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

In this case, the traffic to our web server comes from two sources: a web application and a mobile application:

- **Web app:** uses a combination of server-side language to handles business logic, storage, etc; and client side languages (HTML, CSS, JS) for visual presentation and interactivity.
- **Mobile app:** HTTP protocol is the communication protocol between the mobile app and the web server. JSON is the commonly used API response format to transfer data.

## Database

With the growth of the user base, one server is no longer enough; and we start needing multiple servers: one for web/mobile traffic and another one for the database. Separating web/mobile traffic (the web tier) and database (data tier) servers allows them to be scaled independently.

![](2024-06-03-14-53-13.png)

### Which databases to use?

We can choose between a traditional relational database and a non-relational database.

Relational databases are also called **relational database management system (RDBMS)** or **SQL databases**. The most popular are SQLite, MySQL, PostgreSQL, etc. They represent and store data in tables and rows. We can perform join operations using SQL across different database tables.

Non-relational databases are also called **NoSQL databases**. Popular ones are CouchDB, Neo4J (graph database), Cassandra, Amazon DynamoDB, MongoDB. Join operations are generally not supported in non-relational DBs. These databases are grouped into four categories:

- **key-value stores**
- **graph stores**
- **column stores**
- **document stores**

For most engineers, relational databases are the best option since they have been around for over 40 years, and they have historically worked well.  However, non-relational databases might be the right choice if:

- Your application requires super-low latency: NoSQL databases are designed to handle large volumes of data and provide high performance with low latency. They are more flexible and scalable than relational databases, which can be an advantage in handling unstructured data and frequent data changes.
- Your data is unstructured.
- You only need to serialize and deserialize data, such as JSON or YAML: A real-life example of an application that only requires serialization and deserialization of data is a caching system. A caching system is used to temporarily store frequently accessed data in memory or on disk, in order to reduce the latency and improve the performance of the system. In a caching system, the data is typically stored in a serialized format, such as JSON or binary, in order to minimize the storage size and maximize the retrieval speed. When a request is made for the data, the caching system retrieves the serialized data from memory or disk, deserializes it into the original data structure or object, and returns it to the client.
- You need to store a massive amount of data.

## Bandwith vs Throughput

Bandwidth and throughput are two related but distinct terms in data communication and computing systems.

**Bandwidth:**
Bandwidth refers to the maximum data transfer capacity of a communication channel or network. It is the measure of the amount of data that can be transmitted per unit of time, typically measured in bits per second (bps) or bytes per second (Bps). Bandwidth is determined by the physical characteristics of the communication channel, such as the frequency range, signal-to-noise ratio, and modulation technique. Bandwidth is an upper limit on the amount of data that can be transmitted, but it does not necessarily reflect the actual data transfer rate.

**Throughput:**
Throughput is the measure of the actual amount of data or work that can be processed, transmitted, or received in a given time frame. It is the rate at which a system can complete multiple operations or tasks. In data communication, throughput is typically measured in bits per second (bps) or bytes per second (Bps). Throughput is affected by various factors, such as latency, packet loss, and network congestion, and it is usually lower than the available bandwidth.

In summary, bandwidth is the maximum data transfer capacity of a communication channel or network, while throughput is the actual data transfer rate achieved in a given time frame. Bandwidth is an upper limit on the amount of data that can be transmitted, while throughput is the actual amount of data transmitted. Bandwidth is a theoretical value, while throughput is a measured value.

## Vertical scaling vs horizontal scaling


