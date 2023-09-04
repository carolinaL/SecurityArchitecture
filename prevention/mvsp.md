# Minimum Viable Secure Product


Minimum Viable Secure Product is a minimalistic security checklist for B2B software and business process outsourcing suppliers.

Designed with simplicity in mind, the checklist contains only those controls that must be implemented to ensure minimally viable security posture of a product.

We recommend that all companies building B2B software or otherwise handling sensitive information under its broadest definition implement at least the following controls, and are strongly encouraged to go well beyond them in their security programs.



## 1 Business controls

### 1.1 Vulnerability reports
* Publish the method and/or point of contact for security reports on your website. Example: Using the https://securitytxt.org/)[security.txt] standard
* Develop and document procedures for triaging reported vulnerabilities
* Respond to reports within a reasonable time frame

### 1.2 Customer testing
* On request, enable your customers or their delegates to test the security of your application
* Test on a non-production environment that closely resembles the production environment in functionality
* Ensure non-production environments do not contain production data

### 1.3 Self-assessment

Perform annual (at a minimum) security self-assessments using the latest MVSP release

### 1.4 External testing

Contract a security vendor to perform annual, comprehensive penetration tests on your systems

### 1.5 Training
Implement role-specific security training for your personnel that is relevant to their business function

### 1.6 Compliance
* Comply with all industry security standards relevant to your business such as PCI DSS, HITRUST, ISO27001, and SSAE 18
* Comply with local laws and regulations in jurisdictions applicable to your company and your customers, such as GDPR, Binding Corporate Rules, and Standard Contractual Clauses
* Ensure data localization requirements are implemented in line with local regulations and contractual obligations

### 1.7 Incident handling
* Notify relevant parties about any security breach that affects personal data without undue delay, no later than 72 hours upon discovery
  
Include the following information in the notification:
* Nature of the breach
* Relevant contact information
* Consequences of the breach
* Measures taken, or needing to be taken, to remediate the issue

### 1.8 Data handling
Ensure media sanitization processes based on NIST SP 800-88 (or equivalent) are implemented for storage media holding unencrypted production data

## 2 Application design controls

### 2.1 Single Sign-On
Implement single sign-on using modern, maintained, and industry standard protocols

### 2.2 HTTPS-only

* Redirect traffic from HTTP protocol (port 80) to HTTPS (port 443)

This does not apply to secure protocols designed to run on top of unencrypted connections, such as OCSP

  * Scan and address issues using freely available modern TLS scanning tools
  * Include the Strict-Transport-Security header with a long `max-age` value

  * Set authentication cookies as Secure

### 2.3 Security Headers
Apply appropriate security headers to reduce the application attack surface and limit post exploitation:

  * Set a minimally permissive Content Security Policy
  * Limit the ability to iframe the application by enabling framing controls with X-Frame-Options
    or CSP frame-ancestors
  * Disable caching for APIs and endpoints that return sensitive data

### 2.4 Password policy
If password authentication is used in addition to single sign-on:

  * Do not limit the permitted characters that can be used
  * Do not limit the length of the password to anything below 64 characters
  * Do not use secret questions as a sole password reset requirement
  * Require email verification of a password change request
  * Require the current password in addition to the new password during password change
  * Store passwords in a hashed and salted format using a memory-hard or CPU-hard one-way hash function
  * Enforce appropriate account lockout and brute-force protection on account access

### 2.5 Security libraries

Use modern, maintained, and industry standard frameworks, template languages, or libraries that systemically address implementation weaknesses by escaping the outputs and sanitizing the inputs

  Example: ORM for database access, UI framework for rendering DOM

### 2.6 Dependency Patching

* Ensure third-party dependencies are maintained and up-to-date, with security relevant updates having a severity score of "medium" or higher applied in line with your application patching schedule
* Where dependency patching or upgrades are not possible, equivalent mitigations should be implemented for all components of the application stack

### 2.7 Logging
Keep logs of:

* Authentication events (success and failure)
* Create, Read, Update, and Delete (CRUD) operations on application and system users and objects
* Security relevant configuration changes (including disabling logging)
* Application owner access to customer data (access transparency)

Logs must include user ID, IP address, valid timestamp, type of action performed, and object of this action.
Logs must be stored for at least 30 days, and should not contain sensitive data or payloads.

### 2.8 Encryption
Use modern, maintained, and industry standard means of encryption to protect sensitive data in transit between systems, and at rest in online data storages and backups

## 3 Application implementation controls

### 3.1 List of data

Maintain a list of sensitive data types that the application is expected to process

### 3.2 Data flow diagram
Maintain an up-to-date diagram indicating how sensitive data reaches your systems and where it ends up being stored

### 3.3 Vulnerability prevention

Train your developers and implement development guidelines to prevent at least the following vulnerabilities:

  * Authorization bypass. Example: Accessing other customers' data or admin features from a regular account
  * Insecure session management. Examples: Guessable token; a token stored in an insecure location (e.g. cookie without Secure and HttpOnly flags set)
  * Injections. Examples: SQL injection, NoSQL injection, XXE, OS command injection
  * Cross-site scripting. Examples: Calling insecure JavaScript functions, performing insecure DOM manipulations, echoing back user input into HTML without escaping
  * Cross-site request forgery. Example: Accepting requests with an Origin header from a different domain
  * Handling untrusted data. Example: Reusing data supplied by users within sensitive application contexts

### 3.4 Time to fix vulnerabilities

Produce and deploy patches to address application vulnerabilities that materially impact security within 90 days of discovery

### 3.5 Build and release process

* Must use a version control system and consistent build process that generates provenance describing how the artifact was built (https://slsa.dev/spec/v1.0/levels#build-l1[SLSA Build Level 1])
* Sensitive application credentials and tokens should be stored separately from the application's source code

## 4 Operational controls

### 4.1 Physical access

Validate the physical security of relevant facilities by ensuring the following controls are in place:

  * Layered perimeter controls and interior barriers
  * Managed access to keys
  * Entry and exit logs
  * Appropriate response plan for unauthorized access

### 4.2 Logical access

* Limit sensitive data access exclusively to users with a legitimate need. The data owner must authorize such access
* Deactivate redundant accounts and expired access grants in a timely manner
* Perform regular reviews of access to validate need to know
* Ensure remote access to customer data or production systems requires the use of Multi-Factor Authentication

### 4.3 Subprocessors

* Maintain a list of third-party companies with access to customer data, and make it available to clients and business partners upon request
* Assess third-party companies annually against the latest MVSP release

### 4.4 Backup and Disaster recovery

* Securely backup all data to a different location than where the application is running
* Maintain and test disaster recovery plans in concert with your incident response planning, at least annually or after significant changes

## Attribution
This document is public domain- [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/).

Created by the [MVSP Working Group](https://mvsp.dev/mvsp.en/) /  
[Sources of MVSP Working Group](https://github.com/vendorsec/mvsp)

