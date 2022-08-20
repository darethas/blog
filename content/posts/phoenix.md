---
title: "Understand Phoenix Better by building with its libraries directly"
summary: "Learn and build with the libraries and tools Phoenix rests upon to help you understand it better."
date: 2020-10-08
draft: true
tags: [programming, phoenix, elixir]
---

Phoenix is a wonderful MVC framework for building web applications. Frameworks are scaffolding. They are an opinionated structure for building or acheiving something useful. Sometimes I find working with a framework's building blocks helps me understand it better: what value it's abstractions provide, how they tie together, and finally how I can change things without straying too far, because the other things frameworks do is limit you to a degree. It just helps me plain learn the purpose of the framework better.

In this post we will conduct this exercise by using Phoenix's building blocks to build a JSON API serving content from a database.

We will use elixir's `mix` tool for the administrative tasks, the `cowboy` library for our http server, `jason` for json things, and finally `postgrex` for connecting to a postgresql database. As the series progresses, we will add more and more features, concluding with a frontend.

Let's begin.

## Start with a new mix project

The first thing we will do is start a new mix project.

```sh
mix new holyfathers_api --sup
```
