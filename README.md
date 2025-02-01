# Node.js Server Hang on Long Requests

This repository demonstrates a common issue in Node.js servers: hanging on long-running requests.  The provided `server.js` code simulates a long-running task (5-second delay) without proper asynchronous handling, causing the server to become unresponsive during that time. The solution shows how to handle such requests properly using asynchronous operations.

## Bug

The `server.js` file contains a simple HTTP server.  However, it has a flaw: it blocks the main event loop during a long-running task.  This will prevent the server from handling any new requests while the long task is executing.  This issue is especially relevant when handling large files, database interactions, or external API calls.

## Solution

The `serverSolution.js` file demonstrates a solution to this issue.  By using asynchronous operations (such as `setTimeout` or promises), the server won't get blocked and can handle other requests concurrently.