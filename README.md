# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the `/users/:id` route fails to handle cases where the `id` parameter is not a valid number.

## Bug

The `bug.js` file contains the problematic code.  It attempts to parse the `userId` as an integer without any error checking.  If a non-numeric `userId` is passed, `parseInt(userId)` will return `NaN`, and the subsequent `users.find` operation may throw an error or produce unexpected results.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  It includes error handling to check if `userId` is a valid number.  If it's not, a 400 Bad Request response is sent.  Otherwise, the code proceeds as before, ensuring robust error handling.

## How to reproduce

1. Clone this repository.
2. Run `npm install express`
3. Run `node bug.js`
4. Send a GET request to `/users/abc` (or similar invalid ID) and observe the error. 
5. Run `node bugSolution.js` and send the same request to see the corrected behavior.