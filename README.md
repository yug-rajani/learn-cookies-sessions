# Cookies and Sessions

## Cookies

Run `npm install`.

1. Run the cookies/insecure.js using Node. Load localhost:8000/home in your browser.
2. Navigate to localhost:8000/start?id=stacy. You should see the cookies being set in the browser's console.
3. Navigate to localhost:8000/home. You should see a different message from 1.
4. Run the cookies/mal.js using Node and load localhost:8001/malhome in your browser in a different tab.
5. Navigate to localhost:8000/home. You should see the same message as 1. Not the cookie value.

Why did this happen? Repeat the experiment with cookies/secure.js and see if the same thing happens.
Answer:
- Why did this happen?: Because anyone could see that cookie, programatically read/write the cookie.
- Repeat the experiment with cookies/secure.js and see if the same thing happens: When we set the cookie with httpOnly:true, it makes sure that cookies cannot be saved or modified by anyone programmatically. This ensures that the cookie value remains the same.

## Sessions

Run `npm install`

1. Run the session/insecure.js using Node. Load localhost:8000/ in your browser.
2. Enter name and click submit. You will see a session being created and stored in a cookie. See the console.
3. Run the session/mal.js using Node. Load localhost:8001/malhome in your browser. Will the session ID be displayed in the console?: Yes.
4. Explore the code in session/insecure.js. Identify all potential vulnerabilities.
- Secure flag should be true to avoid man in the middle attacks.
- No hardcoding. Feed input in secret, or store in configuration file. Only the server should have access.
- sameSite should be true

## Static Analysis

1. Setup CodeQL for this repository and inspect the report.
2. [CSRF tokens](https://www.npmjs.com/package/lusca).