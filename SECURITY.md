# Security policy

## Table of Contents

1. [Introduction](#introduction)
2. [Supported Version](#supported-version)
3. [Reporting a Vulnerability](#reporting-a-vulnerability)
4. [Security Design Notes](#security-design-notes)
5. [Project Status and Deployment Warning](#project-status-and-deployment-warning)

## Introduction

This document describes the security policy for the Pastimes Marketplace
project. It explains which version receives security updates, how to
report a vulnerability responsibly, and the security measures currently
built into the application.

Pastimes is an educational portfolio project. It is not a production
system. All statements below describe the current design of the project
and its known limits.

## Supported Version

This repository is an educational portfolio project. Security
improvements are applied to the latest version on the `main` branch.

Only the latest version on the `main` branch is supported. Older
versions, forks, and local copies do not receive security updates.
Users who deploy or test the project should always work from the most
recent `main` branch to receive current security improvements.

## Reporting a Vulnerability

Do not publish credentials, personal information, or exploit details in
a public issue. Contact the repository owner privately with the affected
file, reproduction steps, impact, and a suggested remediation if
available.

When reporting a vulnerability, please include the following details:

- The affected file or files.
- Clear reproduction steps so the issue can be confirmed.
- The potential impact of the issue.
- A suggested remediation, if one is available.

Please keep all sensitive details private until the maintainers have had
a reasonable opportunity to review and address the report.

## Security Design Notes

The following measures are built into the current application design:

- Database settings can be provided through environment variables. This
  avoids hard-coding credentials in source files.
- New passwords use PHP's `password_hash()` and `password_verify()` APIs.
  These functions provide modern, salted password hashing.
- Legacy MD5 demo hashes are upgraded automatically after a successful
  login. This moves older accounts toward stronger hashing over time.
- Authentication queries use prepared statements. This reduces the risk
  of SQL injection during login.
- Sessions receive a new identifier after authentication. This helps
  prevent session fixation attacks.
- Uploaded files and local environment files are excluded from version
  control. This reduces the chance of leaking runtime content or
  credentials through the repository.

These measures improve security but do not make the application
production ready. Other areas of the codebase, including remaining
database queries and upload handling, still require review.

## Project Status and Deployment Warning

The application remains a learning project and has not undergone a
professional penetration test. Do not deploy it to process real
payments or personal information without a complete security review.

A complete security review should cover every state-changing request,
file upload path, database query, and access control check before any
use with real data.

---

END OF DOCUMENT

---
