# Security Policy

## Supported Versions

| Version | Supported          |
|---------|---------------------|
| 1.0.x   | :white_check_mark: Yes |

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please report it privately to avoid disclosing it to the public.

**How to Report**

Please send an email to: [shunsuke@example.com](mailto:shunsuke@example.com)

Include:
* Description of the vulnerability
* Steps to reproduce
* Potential impact

**What to Expect**

* We will acknowledge receipt of your report within 48 hours
* We will provide a detailed response within 7 days
* We will notify you when the issue is fixed
* You will be credited in the security advisory (if desired)

## Security Best Practices

When using Plugin Generator:

1. **Review generated code** before using it in production
2. **Check plugin permissions** before installing plugins
3. **Keep dependencies updated** by running `npm audit` regularly
4. **Use `.gitignore`** to prevent committing sensitive files

## Security Features

* Plugin name validation prevents directory traversal attacks
* `--force` option requires explicit user consent
* No external dependencies for core functionality
* No network calls during plugin generation
