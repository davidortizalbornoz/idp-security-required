# Requerimientos Técnicos IdP — FAPI 2.0 (SFA Chile)

Documento normatico y técnico que evalúa al menos 44 requisitos de seguridad exigibles al Authorization Server (IdentityServer) bajo FAPI 2.0, en el contexto del Sistema de Finanzas Abiertas (SFA) de la CMF de Chile (NCGN.º 514 y su normativa técnica complementaria, basada en el perfil FAPI 2.0 Security Profile + MessageSigning de la OpenID Foundation).

Para cada ítem se entrega:

1. Contexto técnico (definición, diagrama, ejemplos).
2. Obligatoriedad en FAPI 2.0 / SFA Chile.
3. Soporte nativo en Keycloak ≥ 26.x.
4. Recomendaciones de implementación si no está soportado.

## Resumen Ejecutivo · Matriz de Cumplimiento

| # | Requisito |
|---:|---|
| — | [Resumen ejecutivo – Matriz de cumplimiento](docs/index.md#resumen-ejecutivo-matriz-de-cumplimiento) |
| 0 | [Tabla de Acrónimos](docs/index.md#tabla-de-acronimos) |
| 1 | [Compatible con FAPI 2.0](docs/index.md#punto-01-compatible-fapi-20) |
| 2 | [mTLS 1.3](docs/index.md#punto-02-soporte-mtls-13) |
| 3 | [ES256 / PS256](docs/index.md#punto-03-algoritmos-firma-es256-ps256) |
| 4 | [Rotación de Refresh Tokens](docs/index.md#punto-04-rotacion-refresh-tokens) |
| 5 | [Deshabilitar flujos legacy](docs/index.md#punto-05-inhabilitar-flujos-oauth2-legacy) |
| 6 | [Sender-Constrained Tokens](docs/index.md#punto-06-sender-constrained-tokens) |
| 7 | [DPoP](docs/index.md#punto-07-dpop) |
| 8 | [DCR](docs/index.md#punto-08-dcr) |
| 9 | [Consumo de SSA](docs/index.md#punto-09-consumo-ssa) |
| 10 | [JARM](docs/index.md#punto-10-jarm) |
| 11 | [PAR obligatorio](docs/index.md#punto-11-par-obligatorio) |
| 12 | [PKCE obligatorio](docs/index.md#punto-12-pkce-obligatorio) |
| 13 | [OCSP](docs/index.md#punto-13-ocsp) |
| 14 | [OCSP Stapling](docs/index.md#punto-14-ocsp-stapling) |
| 15 | [Consentimiento granular](docs/index.md#punto-15-consentimiento-granular) |
| 16 | [RAR (RFC 9396)](docs/index.md#punto-16-rar) |
| 17 | [Mapeo de scopes ↔ recursos legales](docs/index.md#punto-17-mapeo-scopes) |
| 18 | [Logs criptográficos no-repudiables](docs/index.md#punto-18-logs-trazabilidad) |
| 19 | [Identificación del Issuer en respuestas (RFC 9207)](docs/index.md#punto-19-identificacion-issuer) |
| 20 | [JAR / Request Object firmado (RFC 9101)](docs/index.md#punto-20-jar-request-object) |
| 21 | [Client Authentication: `private_key_jwt` y `tls_client_auth`](docs/index.md#punto-21-client-authentication) |
| 22 | [JWKS rotativo del cliente](docs/index.md#punto-22-jwks-rotativo) |
| 23 | [`aud` y `exp` estrictos en `client_assertion`](docs/index.md#punto-23-aud-exp-estrictos) |
| 24 | <a href="docs/index.md#punto-24-ciba-backchannel">CIBA Backchannel (OIDC Client-Initiated Backchannel Authentication) <span style="background-color:#fee2e2;color:#b91c1c;"><strong>NO APLICABLE</strong></span></a> |
| 25 | <a href="docs/index.md#punto-25-fapi-ciba-pingmode">FAPI CIBA + PingMode <span style="background-color:#fee2e2;color:#b91c1c;"><strong>NO APLICABLE</strong></span></a> |
| 26 | <a href="docs/index.md#punto-26-acr-amr">ACR / AMR — niveles de autenticación <span style="background-color:#fef3c7;color:#a16207;"><strong>EN CONSULTA DE APLICABILIDAD</strong></span></a> |
| 27 | <a href="docs/index.md#punto-27-webauthn-fido2">WebAuthn / FIDO2 para SCA <span style="background-color:#fee2e2;color:#b91c1c;"><strong>NO APLICABLE</strong></span></a> |
| 28 | <a href="docs/index.md#punto-28-session-management">Session Management OIDC + <code>id_token_hint</code> para logout <span style="background-color:#fee2e2;color:#b91c1c;"><strong>NO APLICABLE</strong></span></a> |
| 29 | <a href="docs/index.md#punto-29-front-back-channel-logout">Front-channel / Back-channel logout (RP-Initiated Logout) <span style="background-color:#fee2e2;color:#b91c1c;"><strong>NO APLICABLE</strong></span></a> |
| 30 | [Algoritmos de cifrado JWE](docs/index.md#punto-30-algoritmos-jwe) |
| 31 | [Cripto-agilidad y *post-quantum readiness*](docs/index.md#punto-31-cripto-agilidad) |
| 32 | [Rate limiting y anti-bruteforce](docs/index.md#punto-32-rate-limiting) |
| 33 | <a href="docs/index.md#punto-33-resiliencia-ha">Resiliencia / HA del Authorization Server <span style="background-color:#fef3c7;color:#a16207;"><strong>EN CONSULTA DE APLICABILIDAD</strong></span></a> |
| 34 | <a href="docs/index.md#punto-34-time-synchronization">Time synchronization (NTP) <span style="background-color:#fef3c7;color:#a16207;"><strong>EN CONSULTA DE APLICABILIDAD</strong></span></a> |
| 35 | [Inventario de eventos + retención](docs/index.md#punto-35-inventario-eventos) |
| 36 | [Pen-testing y conformance recurrentes](docs/index.md#punto-36-pen-testing) |
| 37 | [Soporte de `acr=urn:cmf:cl:sfa:psd2-sca`](docs/index.md#punto-37-acr-urn-cmf) |
| 38 | [Notificaciones / "Push notification consent" (event API)](docs/index.md#punto-38-notificaciones) |
| 39 | <a href="docs/index.md#punto-39-mapeo-sub">Mapeo de <code>sub</code> estable y no-PII <span style="background-color:#fef3c7;color:#a16207;"><strong>EN CONSULTA DE APLICABILIDAD</strong></span></a> |
| 40 | [Validación estricta de `redirect_uri` (exact-match)](docs/index.md#punto-40-redirect-uri) |
| 41 | [`request_uri` pre-registered prohibido](docs/index.md#punto-41-request-uri-prohibido) |
| 42 | [Gestión del ciclo de vida del consentimiento (Consent API formal)](docs/index.md#punto-42-consent-api) |
| 43 | [Aislamiento por *tenant* / realm por institución](docs/index.md#punto-43-aislamiento-tenant) |
| 44 | [Política de claves: separación de roles](docs/index.md#punto-44-politica-claves) |
| 45 | [Apéndice A — Stack de extensión recomendado para Keycloak](docs/index.md#apendice-a-stack-keycloak) |
| 46 | [Apéndice B — Comandos de validación](docs/index.md#apendice-b-comandos-validacion) |
| 47 | [Apéndice C — Referencias](docs/index.md#apendice-c-referencias) |
| 48 | [Documento completo](docs/index.md) |