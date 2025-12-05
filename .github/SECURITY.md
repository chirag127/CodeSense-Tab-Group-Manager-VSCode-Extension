# Security Policy

## Supported Versions

We are committed to maintaining a high level of security for `TabGroupManager-VSCode-Extension`. We actively support and patch the latest stable version of the VS Code extension.

| Version | Supported          |
|---------|--------------------|
| Latest  | :white_check_mark: |

## Reporting a Vulnerability

We take security vulnerabilities very seriously. If you discover any security issue within `TabGroupManager-VSCode-Extension`, please report it by following these steps:

1.  **DO NOT** open a public issue. Instead, send a private email to the primary maintainer at **[chirag127@users.noreply.github.com]**.
2.  **Include:**
    *   A clear and concise description of the vulnerability.
    *   The steps to reproduce the vulnerability, if possible.
    *   Your suggested mitigation or fix, if any.
    *   Your contact information so we can follow up.
3.  **Wait for Confirmation:** We will acknowledge receipt of your report within 48 hours.
4.  **Resolution:** We will work diligently to investigate and address the reported vulnerability. We will provide a timeline for a fix and a public disclosure date once a resolution is available.

## Security Best Practices

As a VS Code extension, `TabGroupManager-VSCode-Extension` interacts with the VS Code API. We adhere to the following best practices:

*   **Principle of Least Privilege:** The extension only requests the permissions it needs to function.
*   **Input Validation:** All user inputs and data processed by the extension are validated to prevent injection attacks.
*   **Secure Dependencies:** We regularly audit our dependencies using security scanning tools and update them promptly.
*   **VS Code API Adherence:** We strictly follow VS Code's security guidelines and recommendations for extension development.

Thank you for helping to keep `TabGroupManager-VSCode-Extension` secure!