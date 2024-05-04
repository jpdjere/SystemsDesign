# Chapter 1 - Scale from zero to millions of users

## Single server setup

To start with something simple, let's take a look at a system where everything is running on a single server. The figure below shows a **single server setup** where everything runs on one server: web app, database, cache, etc.

![](2024-05-29-16-37-11.png)

To understand this setup, let's understand the request flow and traffic source:

![](2024-05-29-16-37-48.png)

1. A user attempts to acces a web