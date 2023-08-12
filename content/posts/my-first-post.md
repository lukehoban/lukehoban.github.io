---
title: "Untyped Lambda Calculus, Church Numerals, and the Y Combinator in Go"
date: 2020-02-25T13:44:49-07:00
---

While reviewing a Go API today — I noticed that this intriguing type is representable in the Go type system:

```go
type V func(v V) V
```

If you are like me — you see that type and think “wait, does that mean the [untyped Lambda Calculus](https://en.wikipedia.org/wiki/Lambda_calculus) is representable inside the Go type system?”.

So let’s try...

First we need some concrete values — but there are no base types like int or bool, only the type V — so all we can hope for is [Church encoded](https://en.wikipedia.org/wiki/Church_encoding) values. For booleans:

```go
var tru V = func(x V) V { return func(y V) V { return x } }
var fals V = func(x V) V { return func(y V) V { return y } }
```

And for numbers:

```go
var zero V = func(f V) V { return func(x V) V { return x } }
var one V = func(f V) V { return func(x V) V { return f(x) } }
var two V = func(f V) V { return func(x V) V { return f(f(x)) } }
```

That’s promising. What about some functions?

```go
var plus V = func(m V) V {
    return func(n V) V {
        return func(f V) V {
            return func(x V) V { 
                return m(f)(n(f)(x))
            }
        }
    }
}
var mult V = func(m V) V {
    return func(n V) V {
        return func(f V) V {
            return func(x V) V {
                return m(n(f))(x)
            }
        }
    }
}
var isZero V = func(n V) V {
    return n(func(_ V) V { return fals })(tru)
}
```

But how do we test that these work? Go won’t let us ask whether isZero(zero) == true since both sides of the == are non-nil functions, and there is no notion of equality of functions.

Somehow we need to turn these functions of type V into real bool or int values. Let’s sneak some side-effects into the argument functions so we can observe what they do!

```go
func (f V) toInt() int {
    n := 0
    f(func(v V) V { n++; return v })(func(v V) V { return v })
    return n
}
func (f V) toBool() bool {
    var b bool
    f(func(v V) V {
        b = true
        return v
    })(func(v V) V {
        b = false
        return v
    })(func(v V) V { return v })
    return b
}
```

And what about subtraction — that one’s a little trickier:

```go
var pred V = func(n V) V {
    return func(f V) V {
        return func(x V) V {
            return n(
                func(g V) V { 
                    return func(h V) V { 
                        return h(g(f))
                    }
                })(func(u V) V { 
                    return x
                })(func(u V) V { return u })
	}
    }
}
```

But the real fun is that we can represent the Y combinator directly within this type — so we can even create recursive functions!

```go
var Y V = func(f V) V {
    return (func(x V) V { 
        return func(n V) V { return f(x(x))(n) } 
    })(func(x V) V {
        return func(n V) V { return f(x(x))(n) }
    })
}
```

Took me a few tries to get that one right. Have to be careful to add a layer of thunks (the two ns) to the classical definition to avoid Go’s call-by-value execution leading to unbounded recursion!

All of that — and finally we can write some recursive functions 🎉.

```go
var fact V = Y(func(f V) V {
    return func(n V) V {
        return isZero(n)(
            func(x V) V { return one },
        )(
            func(x V) V { return (mult(n)(f(pred(n)))) },
        )(zero)
    }
})
var fib V = Y(func(f V) V {
    return func(n V) V {
        return isZero(pred(n))(
          func(_ V) V { return n },
        )(
          func(_ V) V { return plus(f(pred(n)))(f(pred(pred(n)))) },
        )(zero)
    }
})
```

Took a few tries on these to get the thunks right on those ones too (gotta make sure to not accidentally run both branches of the conditional!)

And it works!

```go
func Test(t *testing.T) {
	three := plus(two)(one)
	six := mult(two)(three)
	sevenTwenty := fact(six)
	eight := fib(six)
	assert.Equal(t, 3, three.toInt())
	assert.Equal(t, 6, six.toInt())
	assert.Equal(t, true, isZero(zero).toBool())
	assert.Equal(t, false, isZero(one).toBool())
	assert.Equal(t, 720, sevenTwenty.toInt())
	assert.Equal(t, 2, pred(three).toInt())
	assert.Equal(t, false, isZero(pred(two)).toBool())
	assert.Equal(t, 8, eight.toInt())
}
```


Full code:

 {{< gist 0ec2a3dbbb9a13338d338a3fbbb039ff >}} 