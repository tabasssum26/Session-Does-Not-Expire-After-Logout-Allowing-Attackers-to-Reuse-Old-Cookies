# Session-Does-Not-Expire-After-Logout-Allowing-Attackers-to-Reuse-Old-Cookies
Domain: https://www.acceptmission.com/


Overview: I am writing to highlight a critical security vulnerability related to session management on our platform. Specifically, we have identified that session cookies do not expire upon user logout, leaving accounts vulnerable to unauthorized access. This flaw undermines the integrity of the logout functionality, exposing users to potential session hijacking and replay attacks.

Issue Description: During comprehensive testing, it was discovered that the session cookie remains active even after the user logs out. This behavior constitutes a serious security risk, as it allows attackers to reuse valid session cookies to gain unauthorized access to user accounts. In the absence of proper session termination and cookie invalidation mechanisms, this flaw compromises the security of user data and account privacy, making the platform susceptible to malicious exploitation. Immediate remediation is necessary to ensure that session cookies are properly invalidated upon logout, safeguarding user sessions from abuse.

Steps to Reproduce:
1.Navigate to the Sign-Up Page:
Go to https://app.acceptmission.com/signup_company  and click on "Sign In with Email."
2.Login Using Email Credentials:
Enter valid email credentials to log into the platform.
3.Export Cookies Using "EditThisCookie":
Install the "EditThisCookie" browser extension.
After successfully logging in, use the extension to export the session cookies.
4.Test Session Hijacking Across Browsers:
Open a different browser and import the previously exported cookies using the same extension.
You will now have full access to the account without logging in, demonstrating session reuse across browsers.


5.Logout and Test Session Persistence:
Log out from the first browser session. Normally, this should invalidate the session across all browsers.
However, observe that the second browser, where cookies were imported, remains logged in.
6.Reuse Old Cookies Post Logout:
Log back into the platform using a Google account or email, initiating a new session.
Import the old cookies from step 3 again and attempt to access restricted areas.
Observe that the old session cookies still allow full access to the victim's account, provided the victim’s session is still active, proving that session termination is not properly enforced.


Actual Result:
The session cookie remains valid and allows unauthorized access to restricted areas, even after the user logs out.

Impact:
1.	Session Hijacking Risk: Attackers can easily hijack active user sessions by obtaining and reusing old session cookies, even after the user has logged out.
2.	Bypass of Logout Functionality: The logout process does not properly terminate the session, leaving users vulnerable as their accounts remain accessible through stale cookies.
3.	Unauthorized Account Access: Attackers can exploit this flaw to gain unauthorized access to sensitive user data and account functions without needing to authenticate.
4.	Persistence of Old Sessions: Even after a new login, old session cookies remain valid, allowing attackers to re-enter the account unnoticed, leading to repeated unauthorized access.
5.	Increased Risk of Data Theft: If an attacker gains access to session cookies (e.g., through cross-site scripting (XSS), phishing, or network interception), they can steal sensitive information, modify user settings, or perform malicious actions on behalf of the user.
6.	Failure to Enforce Session Security Best Practices: The platform does not adhere to security best practices, such as properly invalidating sessions post-logout, leading to a weak security posture.
7.	Vulnerability to Session Replay Attacks: Attackers can continuously reuse compromised session cookies until the session expires, extending the window of attack and compromising user trust.
8.	High Potential for Exploitation: This vulnerability can be exploited without sophisticated techniques, making it highly attractive for attackers to target accounts at scale.



Reference:
1.	https://hackerone.com/reports/1162443
2.	https://github.com/calcom/cal.com/issues/12483
3.	https://ricardoiramar.medium.com/reusing-cookies-23ed4691122b
