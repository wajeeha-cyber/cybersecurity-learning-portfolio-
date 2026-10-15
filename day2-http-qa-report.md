
# Day 2: HTTP Analysis and Manual QA Testing

## Project Overview

This project documents beginner-level HTTP traffic analysis and manual QA testing using Firefox Developer Tools and curl.

## Testing Environment

- Operating systems: Windows and Kali Linux
- Tools: Firefox Developer Tools, curl
- Practice websites: https://example.com and https://the-internet.herokuapp.com
- Testing scope: Own browser traffic and public practice functionality

## Part 1: HTTP Traffic Analysis

### HTTP Requests and Responses

- HTTP HEAD request to example.com returned status 200.
- Response Content-Type was text/html.
- A GET request was identified using curl verbose output.
- Firefox Network Monitor showed GET / with status 200.
- User-Agent was identified in Request Headers.

### Login Authentication Flow

- Endpoint: /authenticate
- Method: POST
- Request payload contained the username field.
- Response status: 303 See Other
- Redirect Location: /secure
- The browser followed the redirect with GET /secure.

### Cookie and Session Observations

- Cookie header observed in the /secure request.
- Set-Cookie header observed in the /authenticate response.
- HttpOnly attribute: Present
- Secure attribute: Not observed in the inspected Set-Cookie header
- SameSite attribute: Not observed in the inspected Set-Cookie header
- Path attribute: Not observed in the inspected Set-Cookie header

These observations do not independently establish a security vulnerability. Browser defaults, application behavior and additional testing would need to be considered.

## Part 2: Manual QA Test Cases

### TC-007: Invalid Username Validation

- Test URL: https://the-internet.herokuapp.com/login
- Username: wronguser123
- Password: Public demo password
- Expected result: Login should be rejected.
- Actual result: Login was rejected.
- Status: PASS

### TC-008: Empty Password Validation

- Test URL: https://the-internet.herokuapp.com/login
- Username: tomsmith
- Password: Empty
- Expected result: Login should be rejected.
- Actual result: Login was rejected.
- Status: PASS

## Part 3: Learning Assessment

- Day 2 final quiz score: 4/5 (80%).
- Correct topics: POST, HTTP 303, HttpOnly, HTTPS.
- Revision needed: Cookie vs Set-Cookie header direction.

## Limitations

- Testing was limited to publicly available practice functionality and my own browser requests.
- No automated vulnerability scanning or exploitation was performed.
- Storage Inspector examination was not completed.
- No security vulnerability is claimed based solely on the observed cookie attributes.

## Conclusion

I practiced inspecting HTTP methods, status codes, request and response headers, form payloads, redirects and cookies. I also executed two manual QA tests and recorded their expected and actual results. This work strengthened my foundation in web application testing and HTTP security concepts.
