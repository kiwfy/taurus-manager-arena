# Taurus Manager

[![Latest Version](https://img.shields.io/github/v/release/kiwfy/taurus-manager-arena.svg?style=flat-square)](https://github.com/kiwfy/taurus-manager-arena/releases)
[![Build Status](https://img.shields.io/github/workflow/status/kiwfy/taurus-manager-arena/CI?label=ci%20build&style=flat-square)](https://github.com/kiwfy/taurus-manager-arena/actions?query=workflow%3ACI)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

An intuitive Web GUI for [Taurus](https://github.com/leodisarli/disarli-taurus). Built on Express so you can run standalone, or mounted in another app as middleware.

### Features

* Check the health of a queue and its jobs at a glance
* Paginate and filter jobs by their state
* View details and stacktraces of jobs with permalinks
* Restart and retry jobs with one click

### Usage

#### Prerequisites

Copy the .env.dist file to an .env file and set your user and pass. (default is taurus taurus)
Configure your queues in the "queues" key of [`index.json`](src/server/config/index.json).

Queues are JSON objects. Here are the configuration keys that are common to all three configuration ways:

```js
{

  "name": "queue-name",
  "port": 6379,
  "host": "redis-url",
  "hostId": "redis-name"
}
```

The required `name` and `hostId` have to be present in any of the following JSON objects, the optional keys can be present in them.

The three ways in which you can configure the client are:

##### 1. port/host

```js
{
  // hostname or IP
  // required string
  "host": "127.0.0.1",

  // optional number
  // default: 6379
  "port": 6379,

  // optional string
  "password": "hello",

  // optional number
  // default: 0
  "db": 1,
}
```

##### 2. URL

You can also provide a `url` field instead of `host`, `port`, `db` and `password`.

```js
{
  "url": "[redis:]//[[user][:password@]][host][:port][/db-number][?db=db-number[&password=bar[&option=value]]]"
}
```

##### 3. Redis client options

If you need to pass some specific configuration options directly to the redis client library your queue uses, you can also do so.

```js
{
  "redis": {}
}
```

For Taurus, the `redis` key will be directly passed to [`ioredis`](https://github.com/luin/ioredis/blob/master/API.md#new_Redis_new). To use this to connect to a Sentinel cluster, see [here](https://github.com/luin/ioredis/blob/master/README.md#sentinel).


#### Running the server

Run `npm install` to fetch Taurus's dependencies. Then run `npm start` to start the server.

Note that because Taurus is implemented using `async`/`await`, Taurus only currently supports Node `>=7.6`.

### Development

Want to contribute? Great!

The project using a simple code.
Make a change in your file and be careful with your updates!

**Kiwfy - Open your code, open your mind!**
