# API

Mahsumah Cloud is being designed with an API-first direction for developers, platform integrations and automated cloud operations.

The public API surface will expand alongside the platform.

---

## API Vision

The Mahsumah Cloud API is intended to provide programmable access to platform capabilities such as:

- Projects
- Deployments
- Domains
- DNS
- SSL
- Monitoring
- Backups
- Environments
- AI workloads
- Operational status

---

## Conceptual Architecture

```text
Developer Application
        │
        ▼
Mahsumah Cloud API
        │
        ▼
Control Plane
        │
        ├── Projects
        ├── Deployments
        ├── Domains
        ├── SSL
        ├── Monitoring
        ├── Backups
        └── AI Cloud
        │
        ▼
Infrastructure
```

---

## API Base Structure

A future API may follow a structure similar to:

```text
https://api.cloud.mahsumaah.sa/v1/
```

> This endpoint structure is illustrative and should not be treated as a production endpoint until officially published.

---

## Authentication

API access should use secure authentication.

Potential methods may include:

- API tokens
- Service credentials
- OAuth
- Scoped access tokens

Conceptual request:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Tokens should never be committed to source repositories.

---

## Projects

Projects represent application workloads managed through Mahsumah Cloud.

Potential operations may include:

```text
GET    /projects
POST   /projects
GET    /projects/{id}
PATCH  /projects/{id}
DELETE /projects/{id}
```

Example conceptual response:

```json
{
  "id": "project_123",
  "name": "customer-portal",
  "environment": "production",
  "status": "active"
}
```

---

## Deployments

Deployment APIs may provide programmable access to application delivery workflows.

Potential operations:

```text
GET  /projects/{id}/deployments
POST /projects/{id}/deployments
GET  /deployments/{deployment_id}
```

Example conceptual response:

```json
{
  "id": "deploy_456",
  "status": "ready",
  "environment": "production"
}
```

---

## Domains

Potential domain operations may include:

```text
GET    /projects/{id}/domains
POST   /projects/{id}/domains
DELETE /domains/{domain_id}
```

Example:

```json
{
  "domain": "app.example.com",
  "status": "active",
  "ssl": "active"
}
```

---

## SSL

Certificate status may be exposed through the platform API.

Conceptual endpoint:

```text
GET /domains/{domain_id}/certificate
```

Example:

```json
{
  "status": "active",
  "hostname": "app.example.com"
}
```

---

## Monitoring

Monitoring APIs may expose operational workload status.

Potential data may include:

- Application status
- Availability
- Deployment state
- Resource visibility
- Service health

Conceptual request:

```text
GET /projects/{id}/status
```

Example:

```json
{
  "status": "healthy",
  "deployment": "ready",
  "ssl": "active",
  "backup": "healthy"
}
```

---

## Backups

Potential backup operations may include:

```text
GET  /projects/{id}/backups
POST /projects/{id}/backups
POST /backups/{id}/restore
```

Example:

```json
{
  "id": "backup_789",
  "status": "completed",
  "type": "scheduled"
}
```

---

## AI Cloud

Future API capabilities may include AI workload operations.

Potential concepts:

```text
POST /ai/endpoints
GET  /ai/endpoints
GET  /ai/endpoints/{id}
```

Possible use cases:

- Inference endpoint provisioning
- Model management
- AI workload status
- Vector workload configuration

---

## Environments

Applications may use multiple environments.

Example:

```text
development
staging
production
```

Potential endpoint:

```text
GET /projects/{id}/environments
```

---

## API Errors

A consistent error model should make integrations easier to debug.

Example:

```json
{
  "error": {
    "code": "domain_verification_failed",
    "message": "Domain ownership could not be verified."
  }
}
```

---

## HTTP Status Codes

Common API status codes may include:

```text
200  OK
201  Created
202  Accepted
400  Bad Request
401  Unauthorized
403  Forbidden
404  Not Found
409  Conflict
422  Validation Error
429  Too Many Requests
500  Internal Server Error
```

---

## Rate Limiting

Public APIs should protect platform resources through rate limiting.

Clients should be designed to handle:

```text
429 Too Many Requests
```

and retry appropriately.

---

## Pagination

Large collections may use pagination.

Conceptual request:

```text
GET /projects?page=1&limit=20
```

Example response structure:

```json
{
  "data": [],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 0
  }
}
```

---

## Webhooks

Future integrations may use webhooks to notify external systems when platform events occur.

Potential events:

```text
deployment.started
deployment.ready
deployment.failed

domain.verified
ssl.issued

backup.completed
backup.failed

service.degraded
```

Conceptual flow:

```text
Mahsumah Cloud
      │
      ▼
Platform Event
      │
      ▼
Webhook
      │
      ▼
Customer System
```

---

## GitHub Integration

The API layer can eventually support GitHub-connected automation.

```text
GitHub
  │
  ▼
Mahsumah Cloud
  │
  ▼
Build
  │
  ▼
Deployment
  │
  ▼
Production
```

Potential developer tooling includes:

- GitHub Actions
- Deployment API
- Repository integrations
- Automated deployments

---

## SDK Direction

Official SDKs may be introduced as the public API matures.

Potential SDKs:

```text
JavaScript / TypeScript
Python
PHP
```

Example future developer experience:

```javascript
const cloud = new MahsumahCloud({
  token: process.env.MAHSUMAH_TOKEN
});

const projects = await cloud.projects.list();
```

> This example is conceptual and does not represent a currently published SDK.

---

## CLI Direction

The Mahsumah Cloud CLI may eventually provide command-line access to the same platform capabilities.

Conceptual experience:

```bash
mahsumaah login
mahsumaah projects
mahsumaah deploy
mahsumaah status
```

These commands are part of the developer tooling direction and should not be treated as currently available unless officially released.

---

## API Security

API integrations should follow secure practices.

Recommended controls include:

- Never expose API tokens publicly
- Use scoped credentials
- Rotate compromised tokens
- Restrict service permissions
- Protect webhook secrets
- Validate webhook signatures
- Use HTTPS
- Monitor API activity

---

## API Principles

### Predictable

Resources and responses should follow consistent patterns.

### Secure

Authentication and authorization should be built into every protected operation.

### Observable

API-driven operations should remain visible inside the platform.

### Automatable

Developers should be able to integrate cloud operations into their workflows.

### Versioned

Breaking API changes should be managed through versioning.

---

## Current Status

Public Mahsumah Cloud APIs are part of the developer platform roadmap.

This documentation describes the intended architecture and developer experience.

Production endpoints, authentication methods and schemas will be published here when officially available.

---

## Related Documentation

- [Getting Started](../getting-started/)
- [Deployments](../deployments/)
- [Domains](../domains/)
- [Monitoring](../monitoring/)
- [Security](../security/)
- [AI Cloud](../ai-cloud/)

---

[← Mahsumah Cloud Documentation](../README.md)
