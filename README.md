# NETWORKWALKS – WEEK 04
## Cybersecurity & Ethical Hacking Internship

This repository contains my Week 04 practical work for the Networkwalks Cybersecurity & Ethical Hacking Internship.

The assignment focuses on web reconnaissance, PDF security analysis, password recovery and understanding information disclosure risks. The practical environment was prepared using Kali Linux inside Oracle VirtualBox.

---

## Internship Details

| Field | Details |
|---|---|
| Organization | Networkwalks |
| Internship | Cybersecurity & Ethical Hacking |
| Program/Batch | B084D-Networkwalks |
| Domain | Cybersecurity |
| Week | 04 |
| Modules | M1, M2, M3 |

## 1. Objectives

- Perform initial website reconnaissance.
- Gather domain and DNS information.
- Analyse website response headers.
- Explore publicly available website resources.
- Examine PDF password protection.
- Understand PDF hash extraction and password recovery.
- Understand the risks associated with exposed directories and backup files.
- Document the practical activities and observations.

## 2. Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux | Penetration testing environment |
| Oracle VirtualBox | Running Kali Linux |
| WHOIS | Domain registration lookup |
| DIG | DNS record investigation |
| NSLOOKUP | Domain name resolution |
| CURL | HTTP request and header analysis |
| Hash Calculator | PDF hash calculation |
| PDF Password Cracker | Password auditing of training PDFs |
| QPDF | PDF processing |
| ExifTool | PDF metadata examination |

---

# 3. Practical Implementation

# M1 – Initial Access and Reconnaissance

## 3.1 Kali Linux Setup

The first step was setting up Kali Linux using Oracle VirtualBox. After starting the virtual machine, I checked the environment and network connectivity before beginning the practical activities.

**Screenshot 1 – Initial Environment Setup**

<img width="1347" height="835" alt="image" src="https://github.com/user-attachments/assets/85d25e5e-4061-4e0c-ae58-cb8047053883" />
<img width="1317" height="642" alt="image" src="https://github.com/user-attachments/assets/1fe8c4ae-9645-4765-a3e3-f5effadcb087" />
<img width="1910" height="827" alt="image" src="https://github.com/user-attachments/assets/9ffe19ff-cd29-4519-8151-3b84c03164eb" />
<img width="1302" height="847" alt="image" src="https://github.com/user-attachments/assets/d9daca25-c85b-4cf4-8130-b21acd42cd00" />
<img width="1327" height="775" alt="image" src="https://github.com/user-attachments/assets/25f64450-45bc-4a25-b112-902f67c3fbea" />

## 3.2 Target Website

**Target Website:** https://medirozahospital.com

The website was opened in a browser to understand its homepage, layout and publicly visible content.

**Screenshot 2 – Website Homepage**

<img width="1600" height="777" alt="website homapage" src="https://github.com/user-attachments/assets/1ce50551-e753-435f-ade1-58892ea842b0" />

## 3.3 Website Content Exploration

The website's publicly visible sections were explored to understand its structure and navigation.

**Screenshot 3 – Website Contents**

<img width="1600" height="611" alt="website page" src="https://github.com/user-attachments/assets/c4f2f2ea-ab5c-45d4-b8ba-63474deb6149" />

## 3.4 WHOIS Lookup

WHOIS was used to collect publicly available domain registration information.

It provides details such as the domain registrar, registration information and nameservers.

**Command:**

```bash
whois medirozahospital.com
```

**Screenshot 4 – WHOIS Lookup**

<img width="960" height="317" alt="whois command" src="https://github.com/user-attachments/assets/4eae4746-6225-438c-b6d8-9d9d0f8931f5" />

## 3.5 DNS Enumeration Using DIG

DIG was used to examine DNS information associated with the target domain.

It helps identify DNS records and understand how a domain resolves to an IP address.

The domain resolved to the IPv4 address `199.188.201.16`.

**Command:**

```bash
dig medirozahospital.com
```

**Screenshot 5 – DIG Results**

<img width="960" height="352" alt="dig command" src="https://github.com/user-attachments/assets/4f941e5d-9a96-4f8a-bc64-45588735e5d0" />

## 3.6 Domain Resolution Using NSLOOKUP

NSLOOKUP was used to verify the domain's IP address.

It provides another way to check domain name resolution.

**Command:**

```bash
nslookup medirozahospital.com
```

**Screenshot 6 – NSLOOKUP Results**

<img width="582" height="150" alt="nslookup command" src="https://github.com/user-attachments/assets/60e62b2f-7e5e-4e05-82d5-126e3e555b3d" />

## 3.7 HTTP Header Analysis Using CURL

CURL was used to inspect the HTTP response headers returned by the target website.

This helped identify the response status, protocol, content type and server information.

**Command:**

```bash
curl -I https://medirozahospital.com
```

**Observed Results:**
- HTTP Status: 200
- Protocol: HTTP/2
- Content-Type: text/html
- Server: LiteSpeed
- Content-Length: 5445 bytes

**Screenshot 7 – CURL Results**

<img width="1007" height="371" alt="curl command" src="https://github.com/user-attachments/assets/dd161c09-1c06-4b55-98ee-6f12f85e9c7f" />

<img width="827" height="297" alt="curl-i" src="https://github.com/user-attachments/assets/282da35c-e0fe-4a4a-a300-1616550d9fe8" />

## 3.8 Robots.txt and Sitemap Analysis

The robots.txt and sitemap.xml files were examined to understand the publicly declared website structure.

The robots.txt file listed the following paths as disallowed for web crawlers:

- `/patient/`
- `/staff/`
- `/old/`

The sitemap listed four webpages:

- index.html
- about.html
- doctors.html
- contact.html

These findings describe publicly declared website information and do not independently confirm vulnerabilities or access to restricted resources.

## 3.9 M1 Observations

The reconnaissance activities helped me understand how WHOIS, DIG, NSLOOKUP and CURL are used during the initial stages of a website security assessment.

I also explored the website manually and examined its publicly available structure.

---

# M2 – PDF Security Analysis and Password Recovery

## 3.10 Objective

The objective of M2 was to understand PDF password protection, hash extraction and password auditing using the provided training documents.

## 3.11 PDF Hash Calculation

The Hash Calculator was used to calculate the hash associated with a PDF document.

This helped me understand how hashes represent file information and how they can be used in password-auditing workflows.

**Screenshot 8 – PDF Hash Calculator**

<img width="845" height="617" alt="123" src="https://github.com/user-attachments/assets/e1b0e237-48da-4eb6-a181-b775153f851f" />

## 3.12 Password Recovery – PDF 1

The first training PDF was examined using the password-auditing process.

The result demonstrated whether the document password could be recovered using the available password candidates.

**Screenshot 9 – PDF 1 Password Result**

<img width="926" height="877" alt="456" src="https://github.com/user-attachments/assets/7adee85f-f778-45c9-9254-9a8e4061cc2b" />

## 3.13 Password Recovery – PDF 2

The second PDF
- Content type
- Web server information
- Content length

**Command:**

```bash
curl -I https://medirozahospital.com
```

**Observed Results:**

- HTTP Status: 200
- Protocol: HTTP/2
- Content-Type: text/html
- Server: LiteSpeed
- Content-Length: 5445 bytes

**Screenshot 7 – CURL HTTP Header Analysis**

<img width="827" height="297" alt="curl-i" src="https://github.com/user-attachments/assets/3dd57564-aafd-41d0-8433-c7a57966abef" />

## 3.8 M1 Observations

The reconnaissance activities helped me understand how different tools are used to collect publicly available website information.

WHOIS provided domain registration details, DIG and NSLOOKUP helped examine DNS resolution, and CURL provided information about the website's HTTP response.

Exploring the website also helped me understand its publicly visible structure and content.

No security vulnerability was confirmed through these reconnaissance activities alone.

---

# M2 – PDF Security Analysis

## 3.9 Objective

The objective of this module was to understand PDF password protection, hash calculation and password auditing using training documents.

## 3.10 PDF Hash Calculation

A Hash Calculator was used to understand how file hashes are generated.

A hash is a fixed-length value generated from file contents. It can be used to verify file integrity and support password-auditing workflows.

**Screenshot 8 – PDF Hash Calculator**

<img width="845" height="617" alt="123" src="https://github.com/user-attachments/assets/fb8dac2e-b7fc-4a6a-9429-a0be7e7eaa43" />

## 3.11 PDF Password Auditing

Password auditing was performed on three separate training PDF documents to understand how password-protected files can be assessed.

The activity demonstrated that weak passwords may be easier to guess when tested against suitable password candidates.

### PDF 1 – Password Audit

The first PDF document was examined as part of the password auditing exercise.

**Screenshot 9 – PDF 1 Password Audit**

<img width="926" height="877" alt="456" src="https://github.com/user-attachments/assets/9d5ad3f0-8559-4c27-9613-a3404f3f17d9" />

### PDF 2 – Password Audit

The second PDF document was tested separately to understand the password protection mechanism.

**Screenshot 10 – PDF 2 Password Audit**

<img width="921" height="865" alt="789" src="https://github.com/user-attachments/assets/dd0263ab-996c-4f1b-8f4a-85befc122825" />

### PDF 3 – Password Audit

The third PDF document was also examined using the password auditing process.

**Screenshot 11 – PDF 3 Password Audit**

<img width="1187" height="575" alt="1011" src="https://github.com/user-attachments/assets/34ff6001-864b-48e1-831e-aacbf1ae8804" />

*Note: The screenshots document the lab results. Actual passwords and confidential document contents are not included in this repository.*

## 3.12 M2 Observations

This module helped me understand the relationship between file hashes and password auditing.

It also highlighted the importance of using strong passwords to protect confidential PDF documents.

---

# M3 – Information Disclosure and Security Risks

## 3.13 Objective

This module focuses on understanding information disclosure risks associated with publicly visible website resources, directory information and backup files.

## 3.14 Understanding robots.txt

The robots.txt file was examined during website reconnaissance.

It contained the following paths:

- `/patient/`
- `/staff/`
- `/old/`

These entries indicate paths that website crawlers are instructed not to access.

However, robots.txt does not provide access control and does not confirm whether these paths are accessible or vulnerable.

## 3.15 Information Disclosure Risks

Publicly exposed directories and backup files can create security risks if they contain sensitive information.

Some possible risks include:

- Exposure of internal filenames.
- Accidental disclosure of backup files.
- Exposure of confidential organisational information.
- Improperly configured server permissions.

These risks should be assessed only in an authorised training environment using simulated data.

## 3.16 M3 Observations

This module helped me understand why organisations need to properly secure internal directories, backup files and other sensitive resources.

It also highlighted the importance of correct server configurations and access restrictions.

---

# 4. Key Learning Outcomes

Through the Week 04 activities, I gained an understanding of:

- Setting up Kali Linux using VirtualBox.
- Performing initial website reconnaissance.
- Collecting domain information using WHOIS.
- Examining DNS records using DIG.
- Verifying domain resolution using NSLOOKUP.
- Analysing HTTP response headers using CURL.
- Exploring publicly available website content.
- Understanding file hashes and PDF password auditing.
- Learning about information disclosure risks.
- The importance of responsible and authorised security testing.

# 5. Conclusion

Week 04 gave me practical exposure to website reconnaissance and document security concepts.

Working with Kali Linux and different command-line tools helped me understand how technical information about a website can be collected and analysed.

The PDF security exercises also helped me understand file hashes, password protection and the importance of using strong passwords.

Overall, this week's activities improved my understanding of cybersecurity tools, basic security assessment techniques and the importance of handling information responsibly.

---

# 6. Author Details

**Alby John**

B.Tech – Computer Engineering  
Cybersecurity Enthusiast

**Internship:** Cybersecurity & Ethical Hacking  
**Organization:** Networkwalks  
**Program/Batch:** B084D-Networkwalks

**GitHub:** [alby9999](https://github.com/alby9999)

---

*Project completed as part of the Networkwalks Cybersecurity & Ethical Hacking Internship.*
