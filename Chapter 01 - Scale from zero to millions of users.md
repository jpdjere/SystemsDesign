# Chapter 1 - Scale from zero to millions of users

## Single server setup

To start with something simple, let's take a look at a system where everything is running on a single server. The figure below shows a **single server setup** where everything runs on one server: web app, database, cache, etc.

![](2024-05-29-16-37-11.png)

To understand this setup, let's understand the request flow and traffic source:

![](2024-05-29-16-37-48.png)

1. A user attempts to access a website through a domain name, such as `api.mysite.com`. Usually, the Doman Name System (DNS) is a paid service provided by a 3rd party and is not hosted in our server setup.
2. The Internet Protocol (IP) address si returned to the browser or mobile app.
3. Once the client obtains the IP address, HTTP requests done by the user are sent directly to our web server.
4. Our web server returns HTML pages or a JSON response for rendering.