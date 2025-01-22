# Unresponsive Node.js Server Due to Blocking Operation

This repository demonstrates a common issue in Node.js applications: blocking the event loop with a long-running synchronous operation, causing the server to become unresponsive. The `bug.js` file contains the problematic code.  The solution, `bugSolution.js`, shows how to address this using asynchronous operations.

## Bug

The server in `bug.js` simulates a long-running task (5 seconds) within the request handler.  This blocks the event loop, preventing the server from handling other requests during this time.  Any client trying to connect during this period will experience significant delays or timeouts.

## Solution

`bugSolution.js` illustrates how to refactor the code using asynchronous operations.  Instead of a synchronous `while` loop, the solution uses `setTimeout` to simulate the delay without blocking the event loop.  This allows the server to continue handling other requests concurrently.

## How to run

1.  Clone this repository.
2.  Navigate to the directory.
3.  Run the buggy code:
    ```bash
    node bug.js
    ```
4.  Try accessing `http://localhost:3000/` in your browser. Observe the delay. 
5.  Run the fixed code:
    ```bash
    node bugSolution.js
    ```
6.  Access `http://localhost:3000/` again. Observe the improved responsiveness.