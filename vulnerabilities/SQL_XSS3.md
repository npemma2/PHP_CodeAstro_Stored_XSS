fullname from add menbers to list renwal first sql and then xss

add_members.php fullname param
list_renewal.php fullname param

Affected Web App: CodeAstro Membership Management System in PHP

Version: v1.0

Title: SQL Injection and Stored Cross Site Scripting (XSS) vulnerability

Affected Component: /add_members.php and /list_renewal.php <br>
fullname parameter inside add_members.php is vulnerable to SQL Injection
fullname parameter inside list_renewal.php is vulnerable to Cross-Site Scripting

Impact: SQL Injection (SQLi) vulnerability is a serious web security threat. When attackers execute this type of threat by modifying the query sent by the web application to the database, it can lead to the user's account getting hijacked and the attacker retrieving or deleting sensitive information.

Proof of Concept: To reproduce this attack, an attacker can inject a malicious input like *' OR ' 1 = 1* into the id field while deleting the memberships under the Manage Members tab of the application. The payload *' OR ' 1 = 1* gets successfully accepted leading to the attacker being able to erase sensitive information stored under the members data with the provided id.

Remediation: It is important to update CodeAstro Membership Management System by properly sanitizing code variables, using parameterized queries and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected.
