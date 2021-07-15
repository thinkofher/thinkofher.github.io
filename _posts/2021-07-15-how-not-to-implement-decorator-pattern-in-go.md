---
title: "How not to implement a decorator pattern in Go?"
subtitle: "Personal story."
author: thinkofher
website: "https://github.com/thinkofher"
tags: go dev
layout: post
---

Lets assume you have the following interface in your `go` codebase and
you want to implement very popular design pattern called decorator. It's
a great pattern, that allows you to extend existing objects without
breaking down current API.

It's very often my design pattern of choice, when I'm working with some
legacy code.

```go
type Doer interface {
    Do(context.Context) (*DoerResult, error)
}
```

Probably, you also heard about _interface embedding_, so why not try it? What can
go wrong?

```go
type DoerDecorator struct {
    Doer
}
```

After embedding our `Doer` interface inside the decorator, wee need to
override its interface method. We can do it like below.

```go
func (d *DoerDecorator) Do(ctx context.Context) (*DoerResult, error) {
    doSomeThingElse()

    return d.Do()
}
```

And it's not a great idea at all. Also: compiler won't complain about this.
But we should understand further what's happening here.

Our `DoerDecorator` has got `Doer` interface embedded in itself, so it doesn't
need refer to specific field when calling `Do` method. It can be handy very,
but right here it's unforgivable mistake, because it leads to
infinite recursive function call.

`Do` method will call `doSomeThingElse` function and then call `Do` method
which calls `doSomeThingElse` and `Do` method and again and again, forever.

To fix this up we have to replace `return d.Do()` with `return d.Doer.Do()` at
`Do` method of `DoerDecorator`. By doing so we're telling compiler to call
`Do` method of embedded interface instead of calling it's own `Do` method, which
leads us to previously mentioned recursive function call.

If you want to get rid of this and similar mistakes from your codebase, think about
setting up [staticcheck](https://github.com/dominikh/go-tools/tree/master/cmd/staticcheck) in
your project's CI. You will never catch all mistakes at code review (and it's fine we're only humans),
so having additional tools that will seek for common coding mistakes is a great addition.

You can read more about infinite recursive call [here](https://staticcheck.io/docs/checks#SA5007).
