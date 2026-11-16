# PortSwigger-File-Path-Traversal
My practical learning and write-up for a PortSwigger File Path Traversal vulnerability lab.

## Lab Information

- **Platform:** PortSwigger Web Security Academy
- **Vulnerability:** File Path Traversal
- **Lab Level:** Practitioner
- **Lab Name:** File path traversal, traversal sequences stripped with superfluous URL-decode
- **Status:** Solved

## 1. Objective

The objective of this lab was to exploit a file path traversal vulnerability and retrieve the contents of the `/etc/passwd` file from the lab server.

## 2. Tools Used

- Burp Suite Professional
- Burp Proxy
- Burp Repeater
- Web Browser

## 3. Vulnerability Explanation

The application removes path traversal sequences from user input before performing URL decoding.

Due to incorrect input-processing order, double URL encoding can bypass the filtering mechanism.

## 4. Payload Used

```text
..%252f..%252f..%252fetc/passwd
```

## 5. Methodology

1. Opened the PortSwigger lab.
2. Intercepted the image request using Burp Suite Proxy.
3. Identified the `filename` parameter.
4. Sent the request to Burp Repeater.
5. Tested a double URL-encoded path traversal payload.
6. Retrieved the contents of `/etc/passwd`.
7. Successfully completed the lab.

## 6. Impact

An attacker may access files outside the intended image directory if the application does not properly validate file paths.

Depending on file permissions and application configuration, this could expose sensitive information.

## 7. Screenshots

Screenshots demonstrating the lab request and successful completion are available in the `screenshots/` directory.

## 8. Prevention

- Validate user-supplied filenames.
- Use an allowlist of permitted files.
- Canonicalize file paths.
- Ensure resolved paths remain inside the intended directory.
- Apply consistent URL decoding and input validation.

## 9. Key Learnings

- Understanding File Path Traversal.
- Understanding URL Encoding and Double URL Encoding.
- Using Burp Suite Repeater.
- Identifying input validation weaknesses.
- Analyzing HTTP requests and responses.

**Note:** This write-up documents my authorized practice in the PortSwigger Web Security Academy lab environment.
