fullname sql inj in addd_members and removed in edit_member.php

add_members.php fullname parameter
edit_member.php fullname parameter

Affected Web App: CodeAstro Membership Management System in PHP

Version: v1.0

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Component: /add_members.php and /edit_member.php <br>
fullname parameter inside add_members.php is vulnerable to SQL Injection and fullname parameter inside edit_member.php is vulnerable to Cross-Site Scripting (XSS)

Impact: SQL Injection (SQLi) vulnerability is a serious web security threat. When attackers execute this type of threat by modifying the query sent by the web application to the database, it can lead to the user's account getting hijacked and the attacker retrieving or deleting sensitive information.

Proof of Concept: To reproduce this attack, an attacker can inject a malicious input like *' OR ' 1 = 1* into the fullname field while adding the members under the Add Members tab of the application. The payload *' OR ' 1 = 1* gets successfully accepted leading to the attacker being able to insert malicious data into the database of the application. Additionally, when the same member is edited under the Manage Members tab, corresponding data can be retrieved from the database leading to the attacker stealing sensitive information. Moreover, if the malicious input *<script>alert(1)</script>* was inserted in the Add Members tab, this can lead to a Cross-Site Scripting vulnerability when the data is edited and echoed in the Manage Members tab.

Remediation: It is important to update CodeAstro Membership Management System by properly sanitizing code variables, using parameterized queries and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected.
