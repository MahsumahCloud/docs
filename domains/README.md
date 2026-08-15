# Domains

Mahsumah Cloud provides a managed domain layer for connecting applications, services and digital products to production.

---

## Domain Workflow

```text
Domain
  │
  ▼
DNS
  │
  ▼
Mahsumah Cloud
  │
  ▼
SSL
  │
  ▼
Application
```

---

## 1. Add a domain

Attach a domain or subdomain to your project.

Examples:

```text
example.com
app.example.com
api.example.com
portal.example.com
```

A domain represents the public entry point to your application.

---

## 2. Configure DNS

DNS connects your domain to the application infrastructure.

Depending on the deployment, configuration may include:

- A records
- CNAME records
- TXT verification records
- MX records
- Custom DNS records

The required records depend on the application and service configuration.

---

## 3. Verify ownership

Some domain operations may require ownership verification before they can be activated.

Verification can be completed using DNS records or other platform-supported methods.

Example:

```text
TXT
mahsumaah-verification=xxxxxxxx
```

---

## 4. Connect the domain

Once DNS is configured, the domain can be attached to the target application.

```text
app.example.com
      │
      ▼
Mahsumah Cloud
      │
      ▼
Production Application
```

---

## 5. Provision SSL

Production domains should use encrypted HTTPS connections.

Mahsumah Cloud's managed domain workflow is designed to work with SSL provisioning and certificate lifecycle management.

See:

- [SSL](../ssl/)

---

## Domain States

A domain may move through several operational states:

```text
Added
  ↓
Pending Verification
  ↓
DNS Configured
  ↓
Verified
  ↓
SSL Provisioned
  ↓
Active
```

---

## Root Domains and Subdomains

### Root domain

```text
example.com
```

### Subdomain

```text
app.example.com
```

Subdomains can be used to separate different applications and services.

Example:

```text
www.example.com       → Website
app.example.com       → Application
api.example.com       → API
admin.example.com     → Admin Portal
status.example.com    → Status Page
```

---

## DNS Changes

DNS updates may not become visible immediately.

Propagation time can vary depending on:

- DNS provider
- Record TTL
- Resolver caching
- Previous DNS configuration

Avoid unnecessary DNS changes during production migrations.

---

## Domain Cutovers

For production systems, domain cutovers should be planned carefully.

Recommended workflow:

```text
Prepare Application
      ↓
Verify Deployment
      ↓
Configure SSL
      ↓
Prepare DNS
      ↓
Switch DNS
      ↓
Verify Production
```

This reduces the risk of unnecessary downtime.

---

## Domain Security

Domain management should follow several basic practices:

- Use controlled DNS access
- Protect registrar credentials
- Enable account security controls
- Review DNS changes
- Avoid exposing unnecessary records
- Keep certificate configuration current

---

## Common Use Cases

### Web Application

```text
app.company.sa
```

### API

```text
api.company.sa
```

### Business Platform

```text
portal.company.sa
```

### Internal System

```text
erp.company.sa
```

---

## Platform Direction

Mahsumah Cloud is moving toward a unified domain workflow covering:

- Domain registration
- Domain transfers
- DNS management
- Automated SSL
- Domain verification
- Application routing
- Certificate lifecycle

Capabilities will be documented as they become available.

---

## Next Steps

- [Getting Started](../getting-started/)
- [Deployments](../deployments/)
- [SSL](../ssl/)
- [Monitoring](../monitoring/)
- [Security](../security/)

---

[← Mahsumah Cloud Documentation](../README.md)
