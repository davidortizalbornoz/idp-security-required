# Requerimientos Técnicos IdP — FAPI 2.0 (SFA Chile)

Documento normativo y técnico: **44 requisitos de seguridad** para el *Authorization Server* bajo FAPI 2.0 / CMF Chile.

**Documento completo:** [RequerimientosTecnicos_IdP_FAPI20_v1.MD](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD)

**Sitio con menú lateral desplegado:** [GitHub Pages](https://davidortizalbornoz.github.io/idp-security-required/)

> Al abrir este repositorio, el menú inferior muestra todos los puntos navegables sin desplazarse.

---

## Menú de navegación — Resumen Ejecutivo · Matriz de Cumplimiento (Puntos 1–44)

| # | Enlace al requisito |
|---:|---|
| — | [Resumen ejecutivo – Matriz de cumplimiento](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#resumen-ejecutivo-matriz-de-cumplimiento) |
| 1 | [1. Compatible con FAPI 2.0](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-01-compatible-fapi-20) |
| 2 | [2. Soporte mTLS 1.3](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-02-soporte-mtls-13) |
| 3 | [3. Algoritmos de firma ES256 / PS256](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-03-algoritmos-firma-es256-ps256) |
| 4 | [4. Rotación de Refresh Tokens](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-04-rotacion-refresh-tokens) |
| 5 | [5. Inhabilitar flujos OAuth2 legacy](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-05-inhabilitar-flujos-oauth2-legacy) |
| 6 | [6. Sender-Constrained Tokens](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-06-sender-constrained-tokens) |
| 7 | [7. DPoP (Demonstrating Proof-of-Possession)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-07-dpop) |
| 8 | [8. DCR (Dynamic Client Registration)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-08-dcr) |
| 9 | [9. Consumo de Software Statements (SSA)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-09-consumo-ssa) |
| 10 | [10. JARM (JWT Secured Authorization Response Mode)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-10-jarm) |
| 11 | [11. PAR Obligatorio (Pushed Authorization Requests)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-11-par-obligatorio) |
| 12 | [12. PKCE Obligatorio (S256)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-12-pkce-obligatorio) |
| 13 | [13. OCSP (Online Certificate Status Protocol)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-13-ocsp) |
| 14 | [14. OCSP Stapling](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-14-ocsp-stapling) |
| 15 | [15. Consentimiento Granular e Informativo](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-15-consentimiento-granular) |
| 16 | [16. Rich Authorization Requests (RAR – RFC 9396)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-16-rar) |
| 17 | [17. Mapeo de Scopes y Recursos Legales](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-17-mapeo-scopes) |
| 18 | [18. Logs de Trazabilidad Criptográfica (No-repudiables)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-18-logs-trazabilidad) |
| 19 | [19. Identificación del Issuer en respuestas (RFC 9207)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-19-identificacion-issuer) |
| 20 | [20. JAR / Request Object firmado (RFC 9101)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-20-jar-request-object) |
| 21 | [21. Client Authentication: `private_key_jwt` y `tls_client_auth`](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-21-client-authentication) |
| 22 | [22. JWKS rotativo del cliente](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-22-jwks-rotativo) |
| 23 | [23. `aud` y `exp` estrictos en `client_assertion`](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-23-aud-exp-estrictos) |
| 24 | [24. CIBA Backchannel (OIDC Client-Initiated Backchannel Authentication)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-24-ciba-backchannel) |
| 25 | [25. FAPI CIBA + PingMode](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-25-fapi-ciba-pingmode) |
| 26 | [26. ACR / AMR — niveles de autenticación](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-26-acr-amr) |
| 27 | [27. WebAuthn / FIDO2 para SCA](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-27-webauthn-fido2) |
| 28 | [28. Session Management OIDC + `id_token_hint` para logout](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-28-session-management) |
| 29 | [29. Front-channel / Back-channel logout (RP-Initiated Logout)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-29-front-back-channel-logout) |
| 30 | [30. Algoritmos de cifrado JWE](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-30-algoritmos-jwe) |
| 31 | [31. Cripto-agilidad y *post-quantum readiness*](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-31-cripto-agilidad) |
| 32 | [32. Rate limiting y anti-bruteforce](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-32-rate-limiting) |
| 33 | [33. Resiliencia / HA del Authorization Server](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-33-resiliencia-ha) |
| 34 | [34. Time synchronization (NTP)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-34-time-synchronization) |
| 35 | [35. Inventario de eventos + retención](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-35-inventario-eventos) |
| 36 | [36. Pen-testing y conformance recurrentes](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-36-pen-testing) |
| 37 | [37. Soporte de `acr=urn:cmf:cl:sfa:psd2-sca`](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-37-acr-urn-cmf) |
| 38 | [38. Notificaciones / "Push notification consent" (event API)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-38-notificaciones) |
| 39 | [39. Mapeo de `sub` estable y no-PII](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-39-mapeo-sub) |
| 40 | [40. Validación estricta de `redirect_uri` (exact-match)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-40-redirect-uri) |
| 41 | [41. `request_uri` pre-registered prohibido](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-41-request-uri-prohibido) |
| 42 | [42. Gestión del ciclo de vida del consentimiento (Consent API formal)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-42-consent-api) |
| 43 | [43. Aislamiento por *tenant* / realm por institución](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-43-aislamiento-tenant) |
| 44 | [44. Política de claves: separación de roles](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-44-politica-claves) |

---

### Lista rápida (mismos enlaces)

- [Resumen ejecutivo – Matriz de cumplimiento](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#resumen-ejecutivo-matriz-de-cumplimiento)
- [1. Compatible con FAPI 2.0](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-01-compatible-fapi-20)
- [2. Soporte mTLS 1.3](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-02-soporte-mtls-13)
- [3. Algoritmos de firma ES256 / PS256](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-03-algoritmos-firma-es256-ps256)
- [4. Rotación de Refresh Tokens](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-04-rotacion-refresh-tokens)
- [5. Inhabilitar flujos OAuth2 legacy](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-05-inhabilitar-flujos-oauth2-legacy)
- [6. Sender-Constrained Tokens](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-06-sender-constrained-tokens)
- [7. DPoP (Demonstrating Proof-of-Possession)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-07-dpop)
- [8. DCR (Dynamic Client Registration)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-08-dcr)
- [9. Consumo de Software Statements (SSA)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-09-consumo-ssa)
- [10. JARM (JWT Secured Authorization Response Mode)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-10-jarm)
- [11. PAR Obligatorio (Pushed Authorization Requests)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-11-par-obligatorio)
- [12. PKCE Obligatorio (S256)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-12-pkce-obligatorio)
- [13. OCSP (Online Certificate Status Protocol)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-13-ocsp)
- [14. OCSP Stapling](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-14-ocsp-stapling)
- [15. Consentimiento Granular e Informativo](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-15-consentimiento-granular)
- [16. Rich Authorization Requests (RAR – RFC 9396)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-16-rar)
- [17. Mapeo de Scopes y Recursos Legales](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-17-mapeo-scopes)
- [18. Logs de Trazabilidad Criptográfica (No-repudiables)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-18-logs-trazabilidad)
- [19. Identificación del Issuer en respuestas (RFC 9207)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-19-identificacion-issuer)
- [20. JAR / Request Object firmado (RFC 9101)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-20-jar-request-object)
- [21. Client Authentication: `private_key_jwt` y `tls_client_auth`](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-21-client-authentication)
- [22. JWKS rotativo del cliente](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-22-jwks-rotativo)
- [23. `aud` y `exp` estrictos en `client_assertion`](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-23-aud-exp-estrictos)
- [24. CIBA Backchannel (OIDC Client-Initiated Backchannel Authentication)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-24-ciba-backchannel)
- [25. FAPI CIBA + PingMode](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-25-fapi-ciba-pingmode)
- [26. ACR / AMR — niveles de autenticación](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-26-acr-amr)
- [27. WebAuthn / FIDO2 para SCA](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-27-webauthn-fido2)
- [28. Session Management OIDC + `id_token_hint` para logout](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-28-session-management)
- [29. Front-channel / Back-channel logout (RP-Initiated Logout)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-29-front-back-channel-logout)
- [30. Algoritmos de cifrado JWE](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-30-algoritmos-jwe)
- [31. Cripto-agilidad y *post-quantum readiness*](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-31-cripto-agilidad)
- [32. Rate limiting y anti-bruteforce](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-32-rate-limiting)
- [33. Resiliencia / HA del Authorization Server](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-33-resiliencia-ha)
- [34. Time synchronization (NTP)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-34-time-synchronization)
- [35. Inventario de eventos + retención](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-35-inventario-eventos)
- [36. Pen-testing y conformance recurrentes](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-36-pen-testing)
- [37. Soporte de `acr=urn:cmf:cl:sfa:psd2-sca`](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-37-acr-urn-cmf)
- [38. Notificaciones / "Push notification consent" (event API)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-38-notificaciones)
- [39. Mapeo de `sub` estable y no-PII](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-39-mapeo-sub)
- [40. Validación estricta de `redirect_uri` (exact-match)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-40-redirect-uri)
- [41. `request_uri` pre-registered prohibido](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-41-request-uri-prohibido)
- [42. Gestión del ciclo de vida del consentimiento (Consent API formal)](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-42-consent-api)
- [43. Aislamiento por *tenant* / realm por institución](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-43-aislamiento-tenant)
- [44. Política de claves: separación de roles](docs/RequerimientosTecnicos_IdP_FAPI20_v1.MD#punto-44-politica-claves)
