# 🔒 Security Policy

## Reporting Security Vulnerabilities

We take security seriously and appreciate the security community's help in keeping Onyedika LMS secure.

### 📧 Responsible Disclosure

**Do NOT open a public GitHub issue for security vulnerabilities.**

Instead, please report security vulnerabilities by emailing:
- **Primary**: security@onyedika.com
- **Alternative**: maintainers@onyedika.com

### 📋 What to Include

When reporting a vulnerability, please provide:

1. **Description**: Clear description of the vulnerability
2. **Impact**: Potential impact if exploited
3. **Reproduction Steps**: How to reproduce the issue
4. **Affected Version(s)**: Which versions are affected
5. **Suggested Fix**: If you have one (optional)
6. **Your Contact**: Email and preferred communication method

### ⏰ Disclosure Timeline

We follow responsible disclosure practices:

- **Day 0**: Report received and acknowledged
- **Day 1-2**: Initial assessment and triage
- **Day 3-14**: Active investigation and fix development
- **Day 14-30**: Fix testing and validation
- **Day 30+**: Security update release and public disclosure

### 🔐 Security Update Process

1. **Assessment**: Determine severity and impact
2. **Fix**: Develop and test the patch
3. **Release**: Release security update (usually minor version bump)
4. **Announce**: Public security advisory
5. **Communicate**: Notify affected users

### 🎖️ Security Advisories

All security advisories are published in our [GitHub Security Advisories](../../security/advisories).

## 🛡️ Security Best Practices

### Environment Variables

Never commit sensitive information:

```bash
# ✅ Good
DATABASE_URL=postgresql://user:pass@localhost:5432/db
# In .env (git-ignored)

# ❌ Bad
DATABASE_URL=postgresql://user:pass@localhost:5432/db
# Committed to repository
```

Required secrets (set in GitHub):
- `VERCEL_TOKEN`
- `VERCEL_ORG_ID`
- `VERCEL_PROJECT_ID`
- `DATABASE_URL` (production)
- `NEXTAUTH_SECRET`

### API Security

- All API endpoints require authentication (NextAuth)
- Rate limiting enabled
- CORS configured for trusted origins only
- Input validation on all endpoints
- SQL injection prevention

### Database Security

- Database credentials never in code
- Encrypted connections (SSL/TLS)
- Regular backups (daily)
- Access control via IAM
- Audit logging enabled

### Dependency Management

- Automated dependency scanning via Dependabot
- Security updates applied within 24 hours
- Regular `npm audit` checks
- License compliance verified
- Supply chain verification

### Code Security

- Static analysis on every push
- Secret scanning via TruffleHog
- Code review required before merge
- Branch protection rules enforced

## 🔍 Security Scanning

### Automated Checks

Our CI/CD pipeline includes:

- **Dependabot**: Dependency vulnerability detection
- **TruffleHog**: Secret scanning
- **npm audit**: Vulnerability detection
- **License Check**: License compliance verification

Run security checks locally:

```bash
# npm audit
npm audit --audit-level=moderate

# Check for secrets
git log -p --all -S PRIVATE_KEY

# Check dependencies
npm outdated
```

### Manual Security Review

For manual security review:

```bash
# Check for hardcoded credentials
grep -r "password\|secret\|token" --include="*.ts" --include="*.tsx" src/

# Check dependencies for known vulnerabilities
npm audit

# Check for outdated dependencies
npm outdated
```

## 🚨 Incident Response

### If You Discover a Vulnerability

1. **Stop work** on exploiting the vulnerability
2. **Report immediately** via security@onyedika.com
3. **Do not disclose** publicly until we release a fix
4. **Provide details** to help us understand and fix

### Our Response

1. **Triage** within 24 hours
2. **Develop fix** within 5-14 days (depending on severity)
3. **Release** security update
4. **Announce** publicly (if applicable)
5. **Credit** security researcher (if desired)

## 🏆 Bug Bounty Program

Currently, we are not running a formal bug bounty program. However, we greatly appreciate reports of security vulnerabilities and will:

- Acknowledge your report within 24 hours
- Keep you updated on progress
- Credit you in the security advisory (if desired)
- Consider your feedback for future security improvements

## 🔐 Compliance

### Standards

- OWASP Top 10 compliance
- CWE/SANS Top 25 awareness
- GDPR compliant (data protection)
- Secure coding standards

### Certifications

We aim for compliance with:
- SOC 2 Type II (planned)
- ISO 27001 (planned)
- GDPR (implemented)

## 📚 Resources

- [OWASP Security Guidelines](https://owasp.org/)
- [CWE Top 25](https://cwe.mitre.org/top25/)
- [Secure Coding Best Practices](https://github.com/goldbergyoni/nodebestpractices)
- [GitHub Security Documentation](https://docs.github.com/en/code-security)

## 👥 Security Team

- **Lead**: Security Committee
- **On-Call**: Available for critical issues
- **Contact**: security@onyedika.com

## 📝 Changelog

### Changes to This Policy

- **2026-07-24**: Initial security policy created
- Last Updated: 2026-07-24

---

**Thank you for helping keep Onyedika LMS secure!** 🙏

For questions about this policy, please contact security@onyedika.com
