
# Day 3: Broken Access Control Vulnerability Assessment

## Project Information

- **Project:** Web Application Security Testing
- **Platform:** PortSwigger Web Security Academy
- **Lab:** Unprotected Admin Functionality
- **Difficulty:** Apprentice
- **Vulnerability Category:** Broken Access Control
- **OWASP Category:** A01:2021 - Broken Access Control
- **Testing Type:** Authorized Security Training
- **Lab Status:** Solved
- **Assessment Date:** 15 October 2026

## 1. Executive Summary

During an authorized PortSwigger Web Security Academy lab, I identified an administrative interface that was accessible without authentication.

The administrative path was disclosed through the application's publicly accessible robots.txt file.

After navigating to the disclosed path, I was able to access administrative functionality without logging in.

Within the designated training environment, I successfully performed the lab's required user deletion action.

This demonstrated a broken access control vulnerability caused by insufficient server-side authorization checks.

## 2. Vulnerability Title

Unprotected Admin Panel Allows Unauthorized User Deletion

## 3. Vulnerability Description

The application exposes administrative functionality without properly enforcing authentication and authorization.

An unauthenticated user can discover the administrative interface through robots.txt and directly access it.

The application does not adequately restrict sensitive administrative operations to authorized administrators.

As demonstrated in the lab, this weakness allows an unauthenticated user to perform a privileged action, including deleting a user account.

The exposure of the administrative path in robots.txt assists discovery, but the underlying security vulnerability is the missing access control enforcement.

## 4. Affected Functionality

- Administrative interface
- Administrative user management functionality
- User deletion operation

**Environment:** PortSwigger Web Security Academy training lab.

## 5. Steps to Reproduce

The following steps were performed only in the authorized PortSwigger training environment.

1. Open the provided PortSwigger lab website without authenticating.

2. Navigate to the application's `/robots.txt` endpoint.

3. Identify the administrative path disclosed in the file.

4. Open the disclosed administrative path in the browser.

5. Observe that the administrative interface is accessible without authentication.

6. Locate the designated test user `carlos`.

7. Execute the user deletion action as required by the lab.

8. Observe that the action succeeds and the lab displays the solved status.

## 6. Expected Result

The application should prevent unauthenticated and unauthorized users from accessing administrative functionality.

Administrative endpoints should require valid authentication and appropriate administrator permissions.

Unauthorized requests should be rejected.

## 7. Actual Result

The administrative interface was accessible without authentication.

Administrative user management functionality was exposed.

The designated user deletion action was successfully executed in the training environment.

The PortSwigger lab was marked as solved.

**Result: Vulnerability successfully demonstrated.**

## 8. Security Impact

In an application with the same weakness, an unauthorized attacker could potentially:

- Access restricted administrative functionality.
- View administrative information.
- Perform privileged operations.
- Delete user accounts where such functionality is exposed.
- Disrupt normal application operations.

The actual impact depends on the functionality available through the affected administrative endpoints.

## 9. Root Cause Analysis

The primary root cause is insufficient server-side access control enforcement.

The application allows requests to privileged administrative functionality without properly validating whether the requester has the necessary permissions.

Hiding administrative URLs or excluding them from search engine crawling does not provide effective access control.

## 10. Recommended Remediation

1. Require authentication for administrative functionality.

2. Enforce server-side authorization checks on every privileged request.

3. Apply role-based access control where appropriate.

4. Follow the principle of least privilege.

5. Deny unauthorized access by default.

6. Test administrative endpoints against unauthenticated and low-privileged users.

7. Record and monitor sensitive administrative actions.

Removing the administrative path from robots.txt may reduce its visibility, but it does not fix the underlying authorization vulnerability.

## 11. Evidence and Observations

The following observations were recorded during the practical exercise:

- The robots.txt file disclosed an administrative path.
- The administrative interface was accessible without authentication.
- User management functionality was visible.
- The designated training user deletion action succeeded.
- The lab displayed its solved status.

No real-world application or third-party account was targeted.

## 12. Severity Discussion

The demonstrated vulnerability has potentially serious security implications because unauthorized users can perform administrative actions.

However, a formal severity rating would require additional context, including deployment conditions, affected assets, exploitability and business impact.

No CVSS score was calculated for this training exercise.

## 13. Ethical Testing Scope

All testing was conducted within an intentionally vulnerable PortSwigger Web Security Academy lab.

The user deletion action was performed only against the designated test account in the disposable training environment.

No unauthorized testing was conducted against production systems.

## 14. Key Learning Outcomes

Through this practical exercise, I learned:

- How administrative paths can be disclosed through robots.txt.
- Why robots.txt is not an access control mechanism.
- How broken access control can expose privileged functionality.
- The difference between discovering an endpoint and demonstrating unauthorized access.
- How to reproduce and document a security vulnerability.
- Why server-side authorization is essential.
- How to communicate security impact and remediation.

## 15. Conclusion

I successfully completed the PortSwigger Unprotected Admin Functionality lab.

The exercise demonstrated how missing server-side authorization can allow unauthenticated users to access administrative functionality and perform sensitive operations.

This project strengthened my understanding of broken access control, ethical security testing and professional vulnerability reporting.

## References

- PortSwigger Web Security Academy:
  https://portswigger.net/web-security/access-control

- PortSwigger Unprotected Admin Functionality Lab:
  https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality

- OWASP Top 10 - Broken Access Control:
  https://owasp.org/Top10/A01_2021-Broken_Access_Control/
