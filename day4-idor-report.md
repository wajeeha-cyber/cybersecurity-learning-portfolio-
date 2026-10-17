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

The exercise was completed in an authorized training environment.

**Final Status: SOLVED**
