Password hashing: use a memory-hard, well-tested algorithm — Argon2id (recommended) or bcrypt if Argon2 unavailable. These algorithms embed a salt in the hash string so you do not store a separate raw salt.
Never store plaintext passwords. Store the full hashed string (which contains algorithm parameters + salt).
Use parameterized queries / prepared statements or an ORM to prevent SQL injection.
Encrypt sensitive columns at rest (database-level encryption or field-level with KMS/HSM) for things like reset_token_hash if needed.
TLS for transport (DB <-> app and client <-> app) and strong DB credentials.
Account control: failed-attempt count, lockout expiry, last login, audit log.
Password reset: use single-use, short-lifetime tokens stored as a hash (not the token itself).
2FA: store TOTP secret or 2FA method metadata (encrypted).
Rate limiting / logging / alerts.
