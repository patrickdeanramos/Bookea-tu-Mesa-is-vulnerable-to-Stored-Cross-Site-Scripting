# Bookea-tu-Mesa-is-vulnerable-to-Stored-Cross-Site-Scripting
Bookea-tu-Mesa is susceptible to a Stored Cross-Site Scripting (XSS) vulnerability. This flaw allows attackers to inject malicious scripts that execute within the context of a user's session.

Steps to Reproduce:

1. Go to http://localhost/Bookea-tu-Mesa/index.php
2. Enter "<script>alert('XSS');</script>" in the Full Name and submit.
3. The script executes, demonstrating the XSS vulnerability.

<B>Vulnerable Code:</B>
File: insert_reservation.php
Line 11: $Fname = mysqli_real_escape_string($conex, $_POST['Fname']);

<B>Suggested Fix:</B>
$Fname = htmlspecialchars(mysqli_real_escape_string($conex, $_POST['Fname']), ENT_QUOTES, 'UTF-8');

<B>This would sanitize the HTML character.</B>
CVE Consideration: I believe this issue warrants a CVE ID because it poses a significant security risk. I am willing to coordinate with you on the CVE submission process if you agree that this issue meets the criteria.
