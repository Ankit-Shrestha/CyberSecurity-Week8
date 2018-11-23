# Week-8-Project-Pentesting-Live-Targets

Time spent: 8.0 hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red. Link: https://35.184.88.145/

Challenge Goals:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been differentiated by colors: blue,green, and red. Each version has two vulnerabilities which adds upto 6 in total.

## Blue

<b>Vulnerability #1: SQL Injection:</b>

Most of the data input received by these websites is being sanitized properly. However, one of the three sites has one place where the input is not being sanitized before being used in an SQL query. Determine which color has the vulnerability.

 * When command ' OR SLEEP(5)=0--' is typed in the URL, only Blue version of the website shows the salesperson.

GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/SQLI.gif" width="800">

**Vulnerability #2: Session Hijacking/Fixation:**

Two of the three websites expire their active sessions and require users to re-login every 30 minutes. That is probably too aggressive for the real world, but it is better than the third site which allows sessions to be a year old, and never regenerates the session ID, even when the user agent string changes. This makes it vulnerable to both session hijacking and session fixation attacks.

 * PHPSESSIONID from the hackertools is used after the log in. The PHPSESSIONID from one browser while in BLUE version of the website could be copied to different browsers to hijack the session.

GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/Session-Hijacking.gif" width="800">

## Green

<b>Vulnerability #1: Username Enumeration: </b>

A careless developer mistake has created a username enumeration vulnerability. Determine which color has the vulnerability. You can use the existing username "jmonroe99" as a test. Next, figure out what mistake the developer made.

* In the Green version of the website, when a unrecognized username was typed in, the flash message "Log in was unsuccessful" is displayed NOT in bold.

GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/User-Enumeration.gif" width="800">


**Vulnerability #2: Cross-Site Scripting:**

All three sites do a good job of protecting against a reflected XSS attack. However, one of the sites has a mistake which leaves the site vulnerable to a stored XSS attack. A reflected XSS attack would be easy to reveal, while a stored XSS does not provide instant feedback. You will need to log into the admin area and look through the CMS in order to "spring the trap" and find out if your attack succeeded. Determine which color has the vulnerability. Use your name in the XSS so that your results won't be confused with anyone else's (example: <script>alert('Mallory found the XSS!');</script>).

* Script with alert function was passed in the feedback section, and got the pop-up window only in the green version of the website.

GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/Cross-Site-Scripting.gif" width="800">

## Red

<b>Vulnerability #1: Cross-Site Request Forgery: </b>

One of the three sites does not have CSRF protections on the admin area. A clever attacker could design a form which would automatically submit form data to the staff area and take advantage of a logged in user's access permissions. Be the attacker and design a form which will make a change to the spelling of some database content. (For example, change the first user from "James" to "Jim", or change "Alabama" to "Alabamaaaa".) Then point the form action at each of the three sites to find out which color has the vulnerability. Do not neglect to be stealthy with your form—your unsuspecting, logged-in admin should neither see the form nor the results of the form submission.

 * Change the CSRF token to change the user information. This works only with the red version of the website.
 
 GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/Cross-Site-Request-Forgery.gif" width="800">
 

**Vulnerability #2: Insecure Direct Object Reference:**

One of the three sites is missing code which would prevent some sensitive information from being made public. Determine which color has the vulnerability. Then, figure out what the other two sites did correctly to prevent the information leak.

 * This attack allows to see hidden users in the website by the changing the id. when the id is changed to 10 and 11 respectively, the hidden users are revealed in the red version of the website.

 GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/Insecure-Direct-Object-%20Reference.gif">


<b>Bonus Objective 2:</b> Build on Objective #4 (Cross-Site Scripting). Experiment to see if you can use XSS to: a) direct the user to a new URL, b) read cookie data, c) set cookie data.

* Script with links to different websites could be inserted in the feedback section. The users will be redirected to that website without their consent.

GIF Walkthrough:
<img src="https://github.com/Ankit-Shrestha/CyberSecurity-Week8/blob/master/Bonus.gif">


## Resources

GIFs created with [LiceCap](http://www.cockos.com/licecap/).


