# Cybersecurity-week-4-project

# Week 4 Internship Project: Web Application Penetration Test
under the guidance of @NETWORKWALKS and @WaqasKarim CCIE
[Mediroza_Pentest_Report.docx](https://github.com/user-attachments/files/33061330/Mediroza_Pentest_Report.docx)

 This README summarizes an authorized assessment described in the source report. It is intended for educational and portfolio use. Do not test any system without explicit written permission and an agreed scope.

## Project Overview

During Week 1 of my cybersecurity internship, I documented a five-day black-box penetration test of the Mediroza General Hospital patient portal. The assessment identified security weaknesses related to authentication, patient document protection, PDF metadata, and web server configuration.

The report showed how these issues could combine: an authentication weakness exposed patient reports, weak document passwords and retained metadata revealed further information, and a publicly browsable legacy backup directory exposed confidential organizational data. Sensitive records, passwords, and exploit commands are not included in this README.

## Objective

To identify and document security weaknesses within the authorized scope, understand their potential impact, and provide remediation recommendations.

## Scope and Rules of Engagement

- **Assessment type:** Black-box web application penetration test
- **Duration:** Five days, as stated in the report
- **Scope:** The Mediroza General Hospital web portal identified in the report
- **Restrictions:** Testing was limited to the authorized target. Social engineering, denial-of-service testing, and testing outside the agreed scope were excluded.
- **Authorization:** The source report states that written authorization was granted.

## Methodology

1. **Reconnaissance:** Reviewed publicly available site behavior and identified relevant application areas.
2. **Authentication testing:** Compared login responses and assessed input handling.
3. **Access-control review:** Checked whether patient documents were properly protected.
4. **Document security review:** Assessed PDF password strength and checked for sensitive metadata.
5. **Configuration review:** Reviewed discovered legacy paths for exposed directory contents and backup files.
6. **Reporting:** Summarized the risks and documented remediation recommendations.

## Tools Used

The report lists the following tools: `curl`, `ffuf`, `Hydra`, `qpdf`, `exiftool`, `wget`, Networkwalks Hash Calculator, Networkwalks Password Cracker, and ChatGPT for data presentation.

## Findings Summary

The report documented **seven findings: three Critical, two High, and two Medium**.

| # | Finding | Area | Severity |
|---|---|---|---|
| 1 | Username enumeration through differing login responses | Patient login | Medium |
| 2 | SQL injection enabling authentication bypass | Patient login | Critical |
| 3 | Patient reports accessible after authentication bypass | Patient reports | High |
| 4 | Weak passwords protecting patient PDF files | Patient PDFs | High |
| 5 | Sensitive metadata retained in a patient PDF | PDF metadata | Medium |
| 6 | Forgotten backup directory exposed with directory listing enabled | Legacy directory | Critical |
| 7 | Plaintext staff and shareholder information in the exposed database backup | Exposed backup | Critical |

## Attack-Chain Summary

The assessment began with public reconnaissance that identified the patient portal and a legacy directory. Different login responses revealed whether a username existed. The report then documented an authentication weakness that allowed access to the portal without valid credentials.

The portal exposed three protected pathology reports. Weak PDF passwords and retained metadata provided further information, including a reference to the legacy directory. That directory allowed public browsing and exposed an old database backup containing confidential organizational information.

This chain demonstrates how weaknesses in authentication, document protection, metadata handling, and server configuration can combine to increase risk.

## Screenshot Placeholders

Add sanitized screenshots from the report for Figures 1–5. Before publishing, remove or obscure patient identifiers, credentials, session tokens, personal records, and other sensitive information.

- **Figure 1:** robots.txt disclosure and Patient Portal login page
- **Figure 2:** Patient portal showing protected pathology reports
- **Figure 3:** Assessment-tool verification of the login endpoint
- **Figure 4:** First PDF access evidence
- **Figure 5:** Second PDF access evidence

## Remediation Recommendations

1. Use parameterized queries or prepared statements for database operations.
2. Return consistent login error messages to prevent username enumeration.
3. Store patient documents outside the public web root and check authorization for every document request.
4. Use strong, unique document passwords and avoid predictable public file paths.
5. Remove sensitive metadata before distributing documents.
6. Disable directory listing and remove backups from publicly accessible locations.
7. Review potential exposure, address incident-response obligations, and re-test fixes.

## Learning Outcomes

- How information leaks can support later stages of an attack chain.
- Why prepared statements are important for secure authentication.
- Why file access needs its own authorization checks.
- How weak document passwords and metadata can affect confidentiality.
- Why legacy directories and backup storage should be reviewed.
- How to communicate findings through risk, impact, and remediation.
- Why penetration testing requires written authorization and a defined scope.

## Ethical and Legal Notice

This project summarizes an assessment that the source report states was authorized in writing. A publicly accessible website is not permission to test it. Always obtain explicit written authorization, follow the agreed scope, protect collected evidence, minimize personal data, and comply with applicable laws and disclosure requirements.
