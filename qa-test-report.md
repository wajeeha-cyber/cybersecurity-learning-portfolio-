# Manual Website QA Testing Report

**Tester:** Wajeeha
**Project:** Beginner Manual Website QA Testing
**Website:** https://the-internet.herokuapp.com/checkboxes
**Testing Type:** Functional Testing

## Test Case TC-001: Checkbox Functionality

**Objective:** Verify that both checkboxes can be selected and deselected independently.

**Precondition:** The checkbox testing page is loaded successfully.

### Test Steps
1. Open the checkbox testing page.
2. Observe the initial state of both checkboxes.
3. Click Checkbox 1 and observe the result.
4. Click Checkbox 2 and observe the result.
5. Verify that each checkbox can be selected or deselected independently.

### Expected Result
Both checkboxes should respond to clicks and change their selected state independently.

### Actual Result
Checkbox 2 was initially selected. Both checkboxes responded to clicks and could be selected or deselected independently.

**Test Status:** PASS
**Bug Found:** No

### Conclusion
The checkbox functionality worked as expected during this manual test. No functional issue was observed in the tested interactions.

---
**Note:** This report documents one manual functional test, not a complete website security assessment.

## Test Case TC-002: Dropdown Functionality

**Website:** https://the-internet.herokuapp.com/dropdown

**Objective:** Verify that both dropdown options can be selected successfully.

### Test Steps
1. Open the dropdown testing page.
2. Select Option 1.
3. Verify that Option 1 is displayed.
4. Select Option 2.
5. Verify that Option 2 is displayed.

### Expected Result
The dropdown should allow selection of Option 1 and Option 2 and display the selected value correctly.

### Actual Result
Both Option 1 and Option 2 were selected successfully.

**Test Status:** PASS
**Bug Found:** No

## Test Case TC-003: Valid Login

**Website:** https://the-internet.herokuapp.com/login

**Objective:** Verify successful login with valid credentials.

**Test Steps:**
1. Open the login page.
2. Enter the provided valid demo username and password.
3. Click Login.

**Expected Result:** Login succeeds and the Secure Area opens.

**Actual Result:** Login succeeded and the Secure Area opened.

**Test Status:** PASS
**Bug Found:** No

## Test Case TC-004: Invalid Password

**Website:** https://the-internet.herokuapp.com/login

**Objective:** Verify that an incorrect password is rejected.

**Test Steps:**
1. Open the login page.
2. Enter the valid demo username.
3. Enter an incorrect password.
4. Click Login.

**Expected Result:** Login is rejected and an error message appears.

**Actual Result:** Login was rejected and an error message appeared.

**Test Status:** PASS

## Test Case TC-005: Empty Login Fields

**Website:** https://the-internet.herokuapp.com/login

**Objective:** Verify that login is rejected when both username and password fields are empty.

### Test Steps
1. Open the login page.
2. Leave the username field empty.
3. Leave the password field empty.
4. Click Login.

### Expected Result
Login should be rejected when both fields are empty.

### Actual Result
The website displayed an error message and rejected the login attempt.

**Test Status:** PASS
**Bug Found:** No

## Test Case TC-006: Logout and Session Verification

**Website:** https://the-internet.herokuapp.com/login

**Objective:** Verify that logout returns the user to the login page and that the protected page cannot be accessed without logging in again.

### Test Steps
1. Log in using the provided valid demo credentials.
2. Click Logout.
3. Verify that the login page appears.
4. Navigate directly to https://the-internet.herokuapp.com/secure.
5. Observe whether authentication is required.

### Expected Result
After logout, the protected page should not be accessible without logging in again.

### Actual Result
Logout returned the browser to the login page. A subsequent attempt to open /secure resulted in a login page or authentication-required message instead of access to the Secure Area.

**Test Status:** PASS
**Bug Found:** No issue observed.

### Security Learning
This test checked whether the protected page remained inaccessible after logout. It does not establish that all session-management controls are secure.
**Bug Found:** No
