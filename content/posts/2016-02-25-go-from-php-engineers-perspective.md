---
title: Go from PHP engineer's perspective
date: 2016-02-25
description: >
    An introduction to Go programming language from PHP engineer's perspective. Answers few questions, such as why PHP
    alone is not enough, what are the problems PHP engineers struggle with and how some of them can be solved with Go.
---

![Gopher](/gopher.jpg)

As a PHP engineer, have you ever asked yourself whether you need to master other programming languages?

[PHP] has been the language of choice for building a full-stack monolithic applications for many companies and many
years. Furthermore, in the last 5 years frameworks ([Symfony], [Laravel], [Zend]), tools ([Composer], [Monolog]) and
rapidly growing community ([PHP-FIG]) helped many engineers to build enterprise level software applications. Many
companies, such as Facebook, Yahoo!, Wikipedia, Wordpress, Tumblr, had pure PHP in their early days, and that didn't
hold them back from becoming successful over the years.

However, a successful business grows, so grows the number of engineers it needs to support the growth. Organizational
structure of the company indicates that the existing monolith is better be split apart. At some point the strategy
stabilizes and teams now focus on independent services instead.

In this article we will try to evaluate how far can PHP alone take us and where [Go] can step in and solve problems we
will face down the road.

[PHP]: http://php.net/
[Go]: https://golang.org/
[Symfony]: http://symfony.com/
[Laravel]: https://laravel.com/
[Zend]: http://framework.zend.com/
[Composer]: https://getcomposer.org/
[Monolog]: https://github.com/Seldaek/monolog
[PHP-FIG]: http://www.php-fig.org/

<!--more-->


PHP and microservices
---------------------

As a PHP engineer, you know that if you manage to get initialization time on every request down to 30ms in a large
monolithic application, that's great! Add 50-100ms more for the actual request processing, and you have an amazing
overall response time.

Since we plan to break our monolith apart, what will happen if we stick to the same setup for our services? Simple
calculations, and we have 300ms of just bootstrap time if services interacted 10 times with each other during the same
request. What a bad user experience!

While PHP shines in WEB development, its capabilities in microservices architectures are rather immature. Essential
terms, such as timeout handling, health checks, metrics collection, bulkheads, circuit breakers, are often unfamiliar to
a PHP engineer. Most of them you will find in a variety of frameworks in many other languages out of the box. Support
for them in the PHP ecosystem is very poor, if exists at all.


Meet Go
-------

From Wikipedia:

> Go (often referred to as golang) is an open source programming language developed at Google in 2007 by Robert
Griesemer, Rob Pike, and Ken Thompson. Designed primarily for systems programming, it is a compiled, statically typed
language in the tradition of C and C++, with garbage collection, various safety features and CSP-style concurrent
programming features added.

Go was developed at Google. It was not a fun 20% project, neither it was to achieve something that others could not do.
It was simply created out of the frustration of dealing with the complexity generated by very large teams working on
very large pieces of software written in languages with large feature sets.

While it has great features like easy concurrency or fast compilation, the main feature that makes it special is extreme
simplicity. On a related note, the list of keywords counts to [25] compared to [67] in PHP.

Go appeared on the market roughly at the same time when PHP received the support for namespaces (2009). In just 6 years
there're already dozens of great projects, among others [Docker], [Kubernetes], [etcd], [InfluxDB], and tons of
companies like Cloudflare, Google, Dropbox, SoundCloud, Twitter, PayPal that build their backend systems in Go.

[25]: https://golang.org/ref/spec#Keywords
[67]: http://php.net/manual/en/reserved.keywords.php
[Docker]: https://www.docker.com/
[Kubernetes]: http://kubernetes.io/
[etcd]: https://coreos.com/etcd/
[InfluxDB]: https://influxdata.com/time-series-platform/influxdb/


Back to microservices
---------------------

Let's walk through the problems we talked about previously and see what we can benefit from using Go.

Go applications quickly compile to machine code. Many people claim that compiling time is so fast that by the time they
switch to a browser and hit “Refresh”, the application is already recompiled, restarted and serves the request. Even
with large codebases there’s a feeling that you’re working with an interpreted language, just like PHP.

Traditional "Hello, World!" API is written in 10 lines of code and responds in less than a millisecond. Multi-core
capabilities allow engineers to run heavy pieces of their software in parallel. The ecosystem allows to choose any
transport protocol such as [JSON over HTTP], [gRPC], [Protocol Buffers] or [Thrift]. Requests are easily traced in
[Zipkin]. Metrics are exported from [statsd] to [Prometheus]. Enforce incoming or outgoing request throughput with rate
limiters and protect client-service communication with circuit breakers.

[JSON over HTTP]: http://www.jsonrpc.org/historical/json-rpc-over-http.html
[gRPC]: http://www.grpc.io/
[Protocol Buffers]: https://developers.google.com/protocol-buffers/
[Thrift]: https://thrift.apache.org/
[Zipkin]: http://twitter.github.io/zipkin/
[statsd]: https://github.com/etsy/statsd
[Prometheus]: https://prometheus.io/


More about Go
-------------

### Language

Go is a strictly typed language, which requires that you specify the type of the variable during its initialization:

```go
var name string = "sobit"
```

Variables can infer the type of the value on the right hand side. The above code is equal to its shortened versions:

```go
var name = "sobit"

// or even better:

name := "sobit"
```

Now, let’s remember how we swap values of two variables in PHP:

```php
<?php

$buffer = $first;
$first = $second;
$second = $buffer;
```

And here is the equivalent in Go:

```go
first, second = second, first
```

This is possible due to the ability of multiple return values. An example of a multiple return values function:

```go
func getName() (string, string) {
    return "sobit", "akhmedov"
}

first, last = getName()
```

In Go code you won't see so commonly used `foreach`, `while` and `do-while`. They are unified into a single `for`
statement:

```go
// foreach ($bookings as $key => $booking) {}
for key, booking := range bookings {}

// for ($i = 0; $i < count($bookings); $i++) {}
for i := 0; i < len(bookings); i++ {}

// while ($i < count($bookings)) {}
for i < len(bookings) {}

// do {} while (true);
for {}
```

While Go doesn't have something called "class" or "object", it does have a type that matches the same definition of a
data structure that integrates both code and behavior. In Go this is called "struct". Let's use an example to illustrate
it:

```go
type rect struct { // define a struct
    width  int
    height int
}

func (r *rect) area() int { // define a function on struct
    return r.width * r.height
}

r := rect{width: 10, height: 15} // initialize
fmt.Print(r.area())
```

Sometimes it can be useful to define a complex structure as well. Here is an example:

```go
type Employee struct {
    Name string
    Job  Job
}

type Job struct {
    Employer string
    Position string
}

// and to structure it
e := Employee{
    Name: "Sobit",
    Job: {
        Employer: "GetYourGuide",
        Position: "Software Engineer",
    },
}
```

There are tons of other features I’m eager to talk about, but that would have me duplicate the great [Effective Go]
document from the official website and producing a never-ending article. But I would like to take a little moment to
introduce you to the concurrency in Go, which I find to be one of the most interesting topics about the language. Before
we jump in, two things you need to know about concurrency in Go - *goroutines* and *channels*.

A goroutine has a simple model: it is a function executing concurrently with other goroutines in the same address
space. When the call completes, the goroutine exists, silently. Simplest examples is to create a heartbeat function that
will print the "I'm alive" message to the terminal every second:

```go
func heartbeat() {
    for {
        time.Sleep(time.Second)
        fmt.Println("I'm still running...")
    }
}
```

Now, how do we run it so that it executes in the background and allows us to do other things in parallel? The answer is
easier than you might think of, just prefix the call with `go`:

```go
go heartbeat()

// keep doing other stuff
```

The approach is similar to "fire-and-forget" events triggering. But what if we don't need to forget and are interested
in the result the function produces? This is where channels come to play:

```go
func getName(id int, c chan string) {
    c <- someHeavyOperationToFindTheName(id)
}

func main() {
    c := make(chan string, 2) // allocate a channel

    go getName(1, c) // trigger
    go getName(2, c) // don't wait and trigger again

    // keep doing other stuff

    fmt.Printf("Employees: %s, %s", <-c, <-c) // combine
}
```

To summarize, we just triggered the same function twice and let the application execute them in parallel, and asked to
give us back the results at the point where we actually needed them.


[Effective Go]: https://golang.org/doc/effective_go.html

### Tools

Go was designed, again, with the simplicity in mind. Authors took a rather radical approach to solve common activities
engineers do all day long. Say "Goodbye" to the endless "space-vs-tab" battles, code standards from community groups who
are trying to somehow simplify the way engineers share code. Go brings the `go fmt` tool out of the box which takes care
of styling your code. No more sharing of IDE configuration files, no more attempts to remember if the opening brace
should go on the same or on the next line.

The documentation of the package source can be read using `go doc`, while `go vet` will help finding potential problems
in the code. Installing vendor libraries is as easy as running `go get github.com/[vendor]/[package]`, and tests are
executed by triggering `go test [package]` command. As you can see, most of the tools that engineers include to every
application in every language is already here, out of the box.


### Deployment

Deployment is a mandatory action no matter which language you choose or what you're building. Being a PHP engineer, how
many [Capistrano] or [Envoy] configurations have you written in your professional life? How many manually changed files
have you transferred over FTP to your hosting provider back in the days?

This is how the most common and simple PHP deployment process looks like:

- Checkout the latest code on the target server into a new release folder
- Copy cached dependencies and install updated ones
- Copy environment-specific configuration files
- Run all the scripts to warm the application up
- Point the current release symlink into the new release folder
- Restart PHP-FPM

Some teams can take this process into a more advanced level like:

- Checkout the latest code on the build server
- “Build” it (install dependencies, warm the caches up, etc.)
- Create a distributable “artifact” (an archived `tar.gz` file)
- Transfer the artifact to the target server
- Unarchive into a new release folder
- Point the current release symlink into the new release folder
- Restart PHP-FPM

Of course, besides that you need to make sure your target and build servers have at least PHP-FPM and PHP installed, and
they better match their versions between each other as well as the version engineers use for local development.

And now let me introduce the deployment process of a regular Go application:

- Checkout the latest code on the build server
- Build it (note the absence of quotes)
- Transfer the artifact (again no quotes) to the target server
- Restart the running application

And that's it. The only difference between potentially simple and advanced versions is whether to have a standalone
build server for that or not.

The beauty is that you don't even need to have Go installed on your target servers, and even if they are running
different operating systems or based on different CPU architectures, you can still prepare artifacts for all of them
(even for Windows) from a single build server or any other machine.

[Capistrano]: http://capistranorb.com/
[Envoy]: https://laravel.com/docs/master/envoy


Conclusion
----------

It was never recommended to decompose a system into microservices while it is not mature enough. While small, a business
has to be flexible and react quickly to the opportunities in the market. This is not an ideal environment for building
microservices, and more benefits can be achieved by having a monolith instead. PHP with its ecosystem perfectly fits
into this strategy.

When the organization stabilizes and it is easy to identify its bounded contexts, building microservices in PHP to
complement them may be painful. Various tools and techniques exist in many other languages to support such architecture.
You may put yourself into risk to either build your own tools or refuse them completely - both can be costly for your
organization.

On the other hand, building microservices in Go is worth considering. The language is easy to write and understand, its
learning curve is not that steep as with [Java] or [Scala], and the performance is not far behind [C]. The compilation
time keeps engineers efficient, while the support for multi-core or networked machines makes it possible to write
powerful applications.

[Java]: https://www.java.com/en/
[Scala]: http://www.scala-lang.org/
[C]: https://en.wikipedia.org/wiki/C_(programming_language)


Additional resources
--------------------

The best place to land for a new gopher is probably the [learning section] on the official website. It includes an
[interactive introduction to Go] to try it out in your browser as well as the [best practices document] that will help
understanding how to write clear, idiomatic Go code.

If that feels not enough, there's a [collection of community-driven initiatives] to help sharpening newly acquired
skills.

If you're the same fan of [JetBrains] IDEs as I am, check out the excellent [Go plugin for IntelliJ], which is developed
mostly by the same JetBrains developers. It can be installed on almost any of their IDEs, including [PhpStorm]. For
other IDEs and text editors, visit [wiki page].

When you feel like ready to build your first production-ready microservice in Go, I would encourage you to look at [Go
kit]. It is a programming toolkit that strives to solve common problems in distributed systems to let engineers focus
on the business logic.

Least important, but worth mentioning, is the possibility to build client side JavaScript applications using [GopherJS]
and entirely native or SDK [applications for iOS and Android].

[learning section]: https://golang.org/doc/#learning
[interactive introduction to Go]: https://tour.golang.org/
[best practices document]: https://golang.org/doc/effective_go.html
[collection of community-driven initiatives]: https://github.com/golang/go/wiki/Learn
[JetBrains]: https://www.jetbrains.com/
[Go plugin for IntelliJ]: https://github.com/go-lang-plugin-org/go-lang-idea-plugin
[PhpStorm]: https://www.jetbrains.com/phpstorm/
[wiki page]: https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins
[Go kit]: https://github.com/go-kit/kit
[GopherJS]: http://www.gopherjs.org/
[applications for iOS and Android]: https://github.com/golang/go/wiki/Mobile

---

The topic was presented at [GetYourGuide]'s internal tech talk with these slides:

<script async class="speakerdeck-embed" data-id="40a76f07d953493b93663336ccec05a3" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

[GetYourGuide]: http://careers.getyourguide.com/teams/engineering
