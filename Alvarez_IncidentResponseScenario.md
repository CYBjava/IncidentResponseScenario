# Incident Response Scenario: Stolen Company Laptop

> **Scenario:** A finance department employee has their company-issued laptop stolen while at Starbucks. This document outlines the organization's incident response process from identification through post-incident activities.

---

## Table of Contents

- [Scenario Overview](#scenario-overview)
- [1. Identification](#1-identification)
- [2. Detection](#2-detection)
- [3. Containment](#3-containment)
- [4. Eradication](#4-eradication)
- [5. Recovery](#5-recovery)
- [6. Post-Incident](#6-post-incident)
- [Summary](#summary)

---

# Scenario Overview

**Incident:** Stolen laptop incident

- Pretend that an employee had their laptop stolen at Starbucks.

---

# 1. Identification

## 1.1 Communication

- Finance department employee sends an email to IT personnel about the stolen laptop through business email (Microsoft Outlook).

## 1.2 Asset

- Laptop was a company owned laptop that was provided to the employee that has full disk encryption with principle of least privilege access control that has access to MS Suite apps.

## 1.3 Verification Process

- Asset manager checks in with the employee to see if the device can be recovered and determine that it the employee cannot recover the asset.

## 1.4 Reporting

Help Desk I logs the incident in Zendesk (ticketing system) and classifies the incident as medium.

**Help Desk I logs:**

- Device hostname
- Asset ID
- Assigned employee
- Laptop status as powered off
- Last known location in Starbucks

---

# 2. Detection

## 2.1 Device Access

The stolen computer has access to:

- Company financial reports
- Finance documentation dealing with company budgeting
- Internal finance file storage server
- Company network
- VPN

## 2.2 User

- Is not a privileged account.
- PoLP is implemented.

## 2.3 Sessions

Employee states that they had:

- 2 finance files open
- Email open
- Logged on to VPN

Additional information:

- Laptop was locked when left unattended.

---

# 3. Containment

## 3.1 Account Disable

- Finance employee AD account gets disabled by system administrator.

## 3.2 Password Reset

- System administrator resets AD account password.

## 3.3 BitLocker

- Device is encrypted with full disk encryption.
- Company cannot remote wipe without Wi-Fi connection to it.

## 3.4 Network Access

Network administrator performs the following actions:

- Modifies the ACL to prevent the stolen computer's IP from joining the network.
- Implements MAC address filtering to block the device from entering the network.
- Blocks device MAC from entering the VPN gateway.

## 3.5 Device Password

- Password is 12 characters long to unlock device.

## 3.6 Log and Monitoring

- SOC analyst will be notified of the incident and be told to document any login attempt to the network or VPN.

---

# 4. Eradication

## 4.1 Notify Internal Stakeholders

- IT department

## 4.2 Authorities

The theft is reported to local law enforcement by the finance employee.

Information provided:

- Device serial number
- Device description

## 4.3 Device Trust

The following trust relationships are removed:

- Device is removed from the Microsoft service, MS Intune (MDM).
- Remove computer from AD Finance Department OU.
  - Place computer into the Contingent OU.
- Revoke device digital certificate from CA console.
  - Verify that the certificate is located in the Certificate Revocation List (CRL).
- Invalidate Kerberos ticket.

---

# 5. Recovery

## 5.1 Device Leasing

- Finance employee is provided a new company laptop by asset manager.

## 5.2 Backup Data

- Company make a full backup every Monday of the week before company opens and makes an incremental backup throughout the week via AD.
- Finance employee AD home directory was not created, only had the attributes for the path.
- Employee saved important files in MS OneDrive but not anything else.
  - Practice enforced by company.

## 5.3 Enrollment

The employee is granted:

- VPN access
- Network access
- PoLP system access

---

# 6. Post-Incident

## 6.1 Internal Audit

- Perform an audit on user home directory creation.
- Backup any new home directories that are new.
- Perform internal audits bi-annually (Previously annually).

## 6.2 Data Loss Evaluation

Finance employee lost:

- Many minor notes
- A few works in progress reports
- Meeting notes

No critical documents lost.

## 6.3 Policy

- Review IRP to determine what was improved or update to maintain an updated IRP.

## 6.4 Employee Training

- Provide additional training to system administrators.
- Provide training to employees on basic internet usage outside of work and secure practices.

---

# Summary

- Finance department employee gets their laptop stolen at Starbucks.
- Incident response process undergoes.
- In Recovery phase, it is found out that the finance employee didn't have their home directory linked to their AD.
- Internal audit for AD home directory creation.
- Employee training for secure practices.
- Additional training for system administrators.

---

## Security concepts / Software Demonstrated

- Incident Response
- Asset Management
- Active Directory
- Microsoft Intune (MDM)
- BitLocker
- VPN Security
- Network Access Control (ACLs)
- MAC Address Filtering
- Certificate Revocation (PKI)
- Kerberos
- Backup and Recovery
- Security Awareness Training
- Security Operations (SOC)
- Zendesk Ticketing
- Principle of Least Privilege (PoLP)
