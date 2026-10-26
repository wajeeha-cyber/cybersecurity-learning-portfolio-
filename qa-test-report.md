# Manual Website QA Testing | Sample Report

**Tester:** Wajeeha  
**Project type:** Beginner manual functional QA sample  
**Application under test:** [The Internet demo application](https://the-internet.herokuapp.com/)  
**Test areas:** Checkboxes, dropdown, login, logout, and post-logout access behavior  
**Execution date:** Not recorded in the original notes  
**Browser / browser version / OS:** Not recorded in the original QA notes  
**Method:** Manual user-interface checks documented from prior practice

> **Scope note:** This is a reorganized version of the original learning report. It describes the six checks previously documented; it does **not** claim that they have been rerun on the date of this update. This is not a paid client engagement, comprehensive website audit, or penetration test.

## 1. Objective

Check that selected user-facing functions of a public practice website behave as expected, and communicate results in a reproducible format appropriate for an entry-level manual QA sample.

## 2. Scope and Test Environment

| Item | Detail |
| --- | --- |
| Target | \`https://the-internet.herokuapp.com\` |
| Pages used | \`/checkboxes\`, \`/dropdown\`, \`/login\`, \`/secure\` |
| Testing approach | Manual browser interactions |
| Test accounts | Public demo credentials provided by the practice application for its login example |
| In scope | Checkbox state changes; dropdown selections; valid/invalid/blank login; logout and post-logout protected-page behavior |
| Out of scope | Cross-browser and mobile coverage, accessibility audit, performance/load tests, automated tests, and comprehensive security assessment |
| Attachments | No screenshots or network captures were included in the original QA report |

Because the original notes do not identify the browser version, OS, test timestamps, or screenshots, these details are deliberately **not invented** here. Future executions should record them.

## 3. Test Execution Summary

| Test ID | Feature / Scenario | Result | Issue observed? |
| --- | --- | --- | --- |
| TC-001 | Checkboxes can be selected and deselected | PASS | No |
| TC-002 | Dropdown accepts both listed options | PASS | No |
| TC-003 | Valid demo login opens Secure Area | PASS | No |
| TC-004 | Incorrect password is rejected | PASS | No |
| TC-005 | Empty username and password are rejected | PASS | No |
| TC-006 | Logout prevents access to Secure Area without signing in again | PASS | No |

**Summary:** 6 test cases documented, 6 marked PASS, 0 functional defects recorded within these specific checks. This is a **limited sample**; it does not establish that the website is bug-free.

## 4. Detailed Test Cases

### TC-001 — Checkbox Functionality

- **URL:** https://the-internet.herokuapp.com/checkboxes
- **Objective:** Verify that the two checkboxes can be toggled independently.
- **Precondition:** Checkbox demo page is loaded.

**Steps**
1. Open the checkbox page.
2. Observe the initial state of each checkbox.
3. Toggle Checkbox 1.
4. Toggle Checkbox 2.
5. Verify that either can be selected or deselected without changing the other unexpectedly.

**Expected:** Each checkbox independently reflects the user's selection.  
**Observed:** Checkbox 2 was initially selected. Both checkboxes responded to clicks and could be selected or deselected.  
**Result:** **PASS**. No functional issue observed.

### TC-002 — Dropdown Functionality

- **URL:** https://the-internet.herokuapp.com/dropdown
- **Objective:** Check both available dropdown options.

**Steps**
1. Open the dropdown page.
2. Select Option 1 and inspect the displayed selection.
3. Select Option 2 and inspect the displayed selection.

**Expected:** Both options can be selected and the displayed value updates.  
**Observed:** Option 1 and Option 2 were each selected successfully.  
**Result:** **PASS**. No functional issue observed.

### TC-003 — Valid Login

- **URL:** https://the-internet.herokuapp.com/login
- **Objective:** Check the standard successful sign-in flow.

**Steps**
1. Open the login page.
2. Enter the site's published valid demo username and password.
3. Submit the form.
4. Check whether the Secure Area opens.

**Expected:** Valid credentials allow access to the Secure Area.  
**Observed:** Login succeeded and the Secure Area opened.  
**Result:** **PASS**. No functional issue observed.

### TC-004 — Invalid Password

- **URL:** https://the-internet.herokuapp.com/login
- **Objective:** Verify that an incorrect password is rejected.

**Steps**
1. Open the login page.
2. Enter the valid demo username.
3. Enter an incorrect password.
4. Submit the form and inspect the result.

**Expected:** Login fails and an error message appears.  
**Observed:** Login was rejected and an error message appeared.  
**Result:** **PASS**. No functional issue observed.

### TC-005 — Empty Login Fields

- **URL:** https://the-internet.herokuapp.com/login
- **Objective:** Verify that blank credentials cannot sign in.

**Steps**
1. Open the login page.
2. Leave both the username and password fields blank.
3. Submit the form.

**Expected:** The application rejects login with empty credentials.  
**Observed:** An error message appeared and login was rejected.  
**Result:** **PASS**. No functional issue observed.

### TC-006 — Logout and Post-Logout Access

- **URLs:** https://the-internet.herokuapp.com/login and https://the-internet.herokuapp.com/secure
- **Objective:** Check that the login state ends after logout in the tested workflow.

**Steps**
1. Log in with the site's valid demo credentials.
2. Click **Logout**.
3. Observe the landing page.
4. Attempt to open \`/secure\` directly without logging in again.
5. Check whether protected content is shown.

**Expected:** Logout returns the user to the login screen and protected content is not accessible without authenticating again.  
**Observed:** Logout returned to the login page. Revisiting \`/secure\` presented a login page or authentication-required message instead of the Secure Area. The original notes did not record the exact HTTP status.  
**Result:** **PASS** for the tested workflow. No issue observed.

**Security limitation:** This functional check is not a comprehensive session-management security audit. It does not validate cookie invalidation, token rotation, caching, concurrent sessions, or every protected endpoint.

## 5. Defects and Follow-Up

**Confirmed functional defects in the recorded test cases:** None.

A QA report remains useful when tests pass: it documents **what was checked**, **how it was checked**, and **what happened**. Passing these tests does not guarantee coverage beyond the scope above.

For future authorized projects, issues should be documented using this template:

| Field | What to record |
| --- | --- |
| Bug ID / Title | Short and specific description |
| Environment | URL, browser/version, OS, device |
| Preconditions | Account state and required setup |
| Reproduction steps | Numbered actions |
| Expected result | Correct behavior |
| Actual result | Observed incorrect behavior |
| Evidence | Sanitized screenshot, video, or relevant logs |
| Severity / Priority | Justified by scope and actual impact |
| Retest result | Whether the issue persists after a fix |

**Template only:** No issue is being claimed in this section.

## 6. Limitations and Next Improvements

- Only six selected workflows were tested; this was not a site-wide review.
- Test date, browser/version, OS, and screenshots were not recorded in the original notes.
- Responsive behavior, accessibility, localization, and performance were not assessed.
- No automated regression suite was executed.
- Further test runs should record environment metadata, screenshots, boundary inputs, and exact error text/status where useful.
- Any future client testing must have clear authorization and a written, agreed scope.

## 7. Conclusion

This sample demonstrates introductory manual QA practices: defining objectives, writing reproducible test steps, comparing expected and observed outcomes, and acknowledging test coverage limits.

**Final recorded outcome:** 6 of 6 documented checks passed; no functional defects were recorded within those checks.

---

**Portfolio:** [Cybersecurity Learning Portfolio](README.md) · **GitHub:** [@wajeeha-cyber](https://github.com/wajeeha-cyber)
