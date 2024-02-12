---
title: Security overview
description: Keeping customer data safe and secure is a huge responsibility and a top priority for GroupNews. These are the steps we take to keep it safe and secure.
---

# Security overview

## Introduction

Keeping customer data safe and secure is a huge responsibility and a top priority for GroupNews. We work hard to protect our customers from threats. We store all our own sensitive information on the same servers our customers do. We don’t want our information compromised, so we’re motivated by self- preservation as well. Aligning our goals with your goals is the best way to see eye-to-eye on the need to keep everything as secure as we can.

## Access control and organizational security

### Personnel

Everyone at GroupNews is made aware of security concerns and best practices for their systems. Anyone with access to internal systems is required to:

- Use unique strong passwords securely managed by a password manager
- Use two-factor authentication on their accounts

We log all access to all accounts by IP address.

All production server operations hosted on DigitalOcean and Amazon Web Services. We require two factor authentication for console and remote access.

## Data Protection and Privacy

Our [privacy policy is available here](https://groupnews.com/about/policies/privacy). Some highlights regarding our data protection practices are:

### Data Location

Our primary data center, managed by DigitalOcean, is in the United States, in New York City. We also utilize Amazon AWS, and their Virginia based data center. All data is backed up daily. Files that our customers upload are stored on servers that use modern techniques to remove bottlenecks and points of failure. Our software infrastructure is updated regularly with the latest security patches.

### Encryption & SSL

We utilize both in-transit and at-rest encryption for the GroupNews application. Over public networks, we send data using strong encryption. We use SSL certificates issued by LetsEncrypt CA. The connection uses RSA encryption, with ECDHE_ECDSA as the key exchange mechanism. You can check our currently supported ciphers at:

- <https://www.ssllabs.com/ssltest/analyze.html?d=groupnews.com&latest>

Any files which you upload to GroupNews are stored and encrypted at rest. Our file storage system, AWS S3, uses AES-256 encryption.

Our application databases are encrypted at rest using LUKS, utilizing default mode `aes-xts-plain64:sha256`, with a randomly generated with a 512-bit ephemeral key per each instance and each volume. All user passwords are hashed and salted using Bcrypt with a cost factor of 11. Additionally, our databases protected by firewalls, with only white-listed servers able to access them.

Our databases are backed up daily, and those backups are encrypted with a randomly generated key per file. These keys are in turn encrypted with a randomly generated RSA key-encryption key-pair and stored in the header section of each backup segment. The file encryption is performed with AES-256 in CTR mode with HMAC-SHA256 for integrity protection. The key lengths are 256-bit for block encryption, 512-bit for integrity protection, and 3072-bits for the RSA key.

### Virus Scanning

Any files which you upload to the GroupNews application are scanned for viruses before they are made available to end users. GroupNews utilizes [Scanii](https://www.scanii.com) to scan file uploads. Files which are flagged by scans are quarantined and marked for review. Only files which pass our scanning process will be made available to end users.

You can read about Scanii’s threat detection engines and security overview at these links:

- <https://docs.scanii.com/article/122-security-overview>
- <https://docs.scanii.com/article/149-how-do-the-different-detection-engines-work>

### Physical Security

We utilize state of the art data centers from both DigitalOcean and Amazon Web Services, each utilizing the latest in physical and logical security. You can find out more about their compliance at these links:

- <https://aws.amazon.com/compliance/data-center/controls>
- <https://www.digitalocean.com/security/infrastructure-security>

### PCI Compliance

When using a credit card on GroupNews to make payments, your payment information never touches GroupNews servers. It is handled directly by our payment processor, [Stripe](https://stripe.com). Stripe is an industry leader in the payment processing space, so your transactions are always safe, secure, and PCI compliant. Stripe’s compliance documentation can be found at:

- <https://stripe.com/docs/security>

### Law enforcement

GroupNews LLC won’t hand your data over to law enforcement unless a court order says we have to. We reject requests from local and federal law enforcement when they seek data without a court order. And unless we’re legally prevented from it, we’ll always inform you when we receive such requests.

### Data deletion

When you cancel your GroupNews subscription, you can continue using the
platform until the current subscription expires. Once expired, while you will no
longer be able to add any new content to your Group, your content will continue
to be accessible in read-only mode.

When you delete your GroupNews Group, however, all your content will be
permanently deleted from all servers and logs within 30 days. This information
can not be recovered once it has been permanently deleted.

### Monitoring

We have monitoring tools we’ve set up to alert us to outages as well any nefarious activity against our domains. We also audit internal data access. If a GroupNews LLC employee wrongly accesses customer data, they will face penalties ranging from termination to prosecution.

In the unfortunate event that someone malicious successfully mounts an attack on our system, we will immediately notify all affected customers.

## Have a concern? Need to report an incident?

Have you noticed abuse, misuse, an exploit, or experienced an incident with your account? Please [submit a support request](/support).

## Conclusion

We at GroupNews, LLC, recognize the importance of handling customer data with utmost care and responsibility. It is your data, after all! We understand that even momentary possession of your data can significantly impact the success and reputation of our company and platform. This is why we are judicious in our software development process, as well as our vendor selection. Our goal and promise to our customers are to earn their trust and confidence while delivering the highest quality news sharing platform we can.
