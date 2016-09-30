# kville-one
Current gen version of Kirupaville.

* **See it live!: https://kirupa-racquet-club.github.io/kville-one/**
* **Old version:** https://www.kirupa.com/lab/kville/main.htm
* **Discuss:** http://forum.kirupa.com/t/lets-do-something-fun-committed-kville-one/

## Getting Involved

Simply fork this repo under your own github account and edit `/src/plot/index.worker.js`.  This JavaScript file (run as a [web worker](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)) represents the interface to your plot in Kirupaville. It will be passed messages through the `onmessage` handler function which can be responded to by calling the `postMessage` function.  Simply by creating a fork, your plot will automatically be recognized and get displayed in the main [community page](https://kirupa-racquet-club.github.io/kville-one/)!

Right now the interface for message posting is under development, but expect more to come soon!

## Plot Workers Messaging API

All incoming messages to plot workers from the community arrive as JSON objects assigned to the `data` property of the received [event](https://developer.mozilla.org/en-US/docs/Web/API/MessageEvent). These objects have at least a `type` property describing what it is 0 or more additional properties based on the value of type.

**data**:Object

parameter | type | attributes
---|---|---
type | string | required

## Incoming Messages by Type

Each type of message may have properties in addition to `type` associated with it.

### "ping"

A simple, nondescript message to request a response from the plot.

parameter | type | attributes
---|---|---
value | number | required

* **value**: An incrementing integer indicating the number of times the ping message has been sent.

**Example**
```js
{ "type": "ping", "value": 1 }
```
