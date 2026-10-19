# Day 4: Insecure Direct Object Reference (IDOR)

## 1. Lab Information

- **Platform:** PortSwigger Web Security Academy
- **Lab:** Insecure Direct Object References
- **Category:** Broken Access Control
- **Status:** Solved
- **Testing Environment:** Authorized PortSwigger training lab

## 2. Objective

Identify an access control vulnerability in the live chat transcript download functionality, retrieve another user's chat transcript, and use the disclosed credentials to complete the lab.

## 3. Tools Used

- Google Chrome
- Chrome Developer Tools
- Network Tab
- Text Editor

## 4. Methodology

**Step 1: Explore the application**

Opened the lab website and navigated to the Live Chat functionality.

**Step 2: Generate a transcript**

Interacted with the live chat and used the View Transcript feature to download a text file.

**Step 3: Inspect network traffic**

Opened Chrome Developer Tools and navigated to the Network tab.

Observed the HTTP requests generated during the transcript download.

**Step 4: Identify the file reference**

Identified a GET request using a numerical transcript filename.

Example:

`GET /download-transcript/3.txt`

The server returned an HTTP `200 OK` response.

**Step 5: Test access control**

Modified the numerical identifier in the transcript URL within the authorized lab.

Example:

`GET /download-transcript/1.txt`

This demonstrated how changing a direct object reference could expose a transcript belonging to another user.

**Step 6: Complete the lab**

Used the information exposed through the vulnerable transcript functionality to complete the lab's authentication objective.

**Result:** Lab successfully solved.

## 5. Vulnerability Analysis

**Vulnerability:** Insecure Direct Object Reference (IDOR)

**Root Cause:** The application allowed transcript files to be accessed through predictable identifiers without adequately verifying whether the requesting user was authorized to access the referenced file.

**Potential Security Impact:**

- Unauthorized disclosure of private conversations
- Exposure of sensitive information
- Possible credential leakage
- Potential account compromise

## 6. Recommended Remediation

1. Enforce server-side authorization checks for every transcript request.
2. Verify that the authenticated user owns or is authorized to access the requested transcript.
3. Return `403 Forbidden` when access is unauthorized.
4. Avoid exposing sensitive credentials in chat transcripts.
5. Use non-predictable identifiers as an additional protective measure, not as a replacement for authorization.

## 7. Key Learnings

- HTTP `200 OK` confirms successful retrieval but does not prove that access was authorized.
- Changing an object identifier can reveal missing authorization checks.
- Predictable filenames can make unauthorized object discovery easier.
- Access control must be enforced on the server.
- Browser Developer Tools can help identify requests associated with sensitive application features.

## 8. Conclusion

This exercise demonstrated an IDOR vulnerability in the chat transcript download functionality.

By inspecting HTTP requests and modifying a file identifier, I learned how insufficient server-side authorization can expose another user's information.

---

# Lab 2: User ID Controlled by Request Parameter with Unpredictable User IDs

## 1. Lab Information

- **Platform:** PortSwigger Web Security Academy
- **Vulnerability:** Broken Access Control / IDOR
- **Difficulty:** Apprentice
- **Status:** Solved
- **Environment:** Authorized training lab

## 2. Objective

Investigate an access control vulnerability involving unpredictable user IDs (UUIDs) and access another user's sensitive account information.

## 3. Tools Used

- Web Browser
- Browser Address Bar
- Browser Developer Tools
- Text Editor

## 4. Testing Methodology

**Step 1: Application Reconnaissance**

Explored the website's blog posts and inspected the author profile links.

**Step 2: User ID Discovery**

Identified that author profile URLs exposed user identifiers in UUID format.

Located the target user `carlos` through the blog functionality and recorded his UUID.

**Step 3: Authenticated Access**

Logged in using the provided lab credentials:

- Username: `wiener`
- Password: `peter`

Opened the My Account page and inspected the `id` request parameter.

**Step 4: Authorization Testing**

Observed the following URL structure:

`/my-account?id=<USER_UUID>`

Replaced the authenticated user's UUID with Carlos's UUID.

**Step 5: Vulnerability Confirmation**

The application allowed access to another user's account information through the modified request parameter.

Successfully completed the lab.

## 5. Root Cause

The application relied on a user-controlled identifier without adequately verifying that the authenticated user was authorized to access the requested account.

Using unpredictable UUIDs did not prevent unauthorized access.

## 6. Security Impact

- Unauthorized access to another user's account information
- Exposure of sensitive account data
- Potential credential or API key disclosure
- Violation of user confidentiality

## 7. Recommended Remediation

1. Implement server-side authorization checks for every account request.
2. Verify the authenticated user's permission to access the requested account.
3. Return `403 Forbidden` for unauthorized access attempts.
4. Avoid treating unpredictable identifiers as an authorization mechanism.
5. Test access controls across different user accounts.

## 8. Key Learnings

- UUIDs can make identifiers harder to guess but do not replace authorization.
- Public pages can reveal identifiers used by protected application features.
- Authentication and authorization are different security controls.
- IDOR vulnerabilities may expose sensitive information even when object identifiers are unpredictable.

## 9. Final Result

**Lab Status: SOLVED**

Successfully investigated and demonstrated an IDOR vulnerability involving unpredictable user identifiers in an authorized training environment.
## Lab 3: Exploiting an API Endpoint Using Documentation

**Platform:** PortSwigger Web Security Academy  
**Category:** API Security / Broken Access Control  
**Tool:** Burp Suite Community Edition  
**Status:** Solved (Guided)

### Objective
Discover exposed API documentation and use the documented functionality to delete the lab user `carlos`.

### Methodology
1. Logged into the lab using the provided test credentials.
2. Inspected HTTP requests using Burp Proxy and Repeater.
3. Requested `/api` and observed a `302` redirect to `/api/`.
4. Requested `/api/` and received `200 OK`.
5. Opened the exposed API documentation in a browser.
6. Identified the documented user deletion functionality.
7. Submitted the following request through the documentation interface:

   `DELETE /api/user/carlos`

8. Observed a `200 OK` response and confirmation that the lab was solved.

### Security Impact
Insufficient authorization checks on sensitive API operations can allow unauthorized users to perform destructive actions, including deleting other users' accounts.

### Recommended Remediation
- Enforce server-side authorization checks on every sensitive API endpoint.
- Restrict account deletion functionality to appropriately authorized users.
- Protect API documentation where appropriate, without relying on documentation secrecy as the primary security control.
- Test access controls for different user roles.

### Key Learnings
- API documentation can expose functionality not visible in the normal website interface.
- HTTP redirects provide useful reconnaissance clues.
- Burp Repeater helps investigate endpoint behavior.
- Successful API responses must be evaluated alongside authorization requirements.

**Learning Method:** Guided lab completion, followed by independent identification of the DELETE request in Burp HTTP History.

The exercise was completed in an authorized training environment.

**Final Status: SOLVED**
