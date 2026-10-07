# Sanitization rules

The public repository must never contain:

- Production credentials or tokens
- Private keys or certificates
- Internal DNS names
- Internal IP addresses
- Real database names/users/hosts
- LDAP bind identities or real group names
- Internal email addresses
- Customer or employee data
- Production dashboard JSON containing internal data
- Private registry credentials
- Organization-specific proprietary scripts/configuration

Use placeholders such as `example.com`, `postgres.example.internal`, and Kubernetes Secret references.
