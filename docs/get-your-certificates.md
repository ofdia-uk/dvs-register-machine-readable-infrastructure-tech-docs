> [!CAUTION]
> **Work in progress**
>
> This documentation is a work in progress and is subject to change.

# Get your certificates

You'll use a transport certificate and a signing certificate to authenticate when you use the DVS register machine-readable infrastructure APIs. You'll get both through the portal.

You do not need these certificates to check another DVS provider's certification. The federation's endpoints are open, which is the default in [OpenID Federation 1.1](https://openid.net/specs/openid-federation-1_1.html#name-client-authentication-at-fe), so anyone can use them without authenticating. Find out how to [check another provider's certification](check-another-provider.md).

## Before you start

You must be a certified DVS provider on the UK [register of digital identity and attribute services](https://www.digital-identity-services-register.service.gov.uk/).

If you're a public authority, read the [information for public authorities](public-authorities.md).

> [!NOTE]
> **Information to follow**
>
> We'll publish how to get access to the portal.

## Understand your certificates

Both certificates are issued by an intermediate certificate authority (CA). The OfDIA root CA issues the intermediate CA's certificate.

| Certificate | What you use it for |
| --- | --- |
| Transport certificate | Authenticating with mutual TLS (mTLS), by presenting it when you open a TLS connection to one of the register's APIs |
| Signing certificate | Signing JSON Web Tokens (JWTs), such as the client assertion you send when you authenticate with `private_key_jwt` |

Your certificates are separate from your [federation entity keys](join-the-federation.md#create-your-federation-entity-keys). You should not use the keys for your certificates to sign your entity configuration.

## Generate your certificates

You'll generate your transport and signing certificates in the portal.

Your certificate keys can use either:

- RSA, with a key size of 2048 bits or more
- ECDSA, with the P-256 or P-384 curve

> [!NOTE]
> **Information to follow**
>
> We'll publish step-by-step instructions for generating your certificates, including:
>
> - any other key and certificate requirements
> - what information your certificates will contain

## Choose how you authenticate

You can authenticate to the machine-readable DVS register's APIs using either:

- [mTLS](#mutual-tls-mtls)
- [`private_key_jwt`](#private_key_jwt)

You should choose the method that best suits your systems.

### Mutual TLS (mTLS)

With mTLS, you present your transport certificate when you open a TLS connection to the register's API. This lets the register confirm that your certificate was issued under the OfDIA root CA, and that you hold its private key.

mTLS client authentication is defined in [RFC 8705](https://www.rfc-editor.org/rfc/rfc8705).

### private_key_jwt

With `private_key_jwt`, you sign a JWT using the private key for your signing certificate. You send the signed JWT as a client assertion, as described in [section 9 of OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html#ClientAuthentication).

The register verifies the signature using the public key from your signing certificate.

> [!NOTE]
> **Information to follow**
>
> We'll publish the details of each authentication method, including:
>
> - which of the register's APIs you'll use your certificates for
> - which of those APIs accept each method
> - how you'll be identified when you authenticate, such as a client identifier

## Keep your private keys secure

You should keep the private keys for your certificates secure. Only the systems that need to authenticate to the register should be able to use them.

You should follow the National Cyber Security Centre (NCSC) guidance on [protecting your private keys](https://www.ncsc.gov.uk/collection/in-house-public-key-infrastructure/pki-principles/protect-your-private-keys), which is part of its guidance on privately hosted public key infrastructure.

## Renew your certificates

You should plan how you'll renew your certificates before they expire, without interrupting your service.

> [!NOTE]
> **Information to follow**
>
> We'll publish:
>
> - how long your certificates will be valid for
> - how to renew your certificates
> - when certificates will be revoked, and what to do if you think a private key has been compromised

## Check whether a certificate has been revoked

The machine-readable infrastructure publishes the revocation status of the certificates issued through the portal using both:

- the Online Certificate Status Protocol (OCSP), defined in [RFC 6960](https://www.rfc-editor.org/rfc/rfc6960)
- certificate revocation lists (CRLs), defined in [RFC 5280](https://www.rfc-editor.org/rfc/rfc5280)

> [!NOTE]
> **Information to follow**
>
> We'll publish the locations of the OCSP responder and the CRLs.

<!-- pagination:start -->

---

- Previous: [How trust works in the machine-readable DVS register](how-trust-works.md)
- Next: [Join the federation](join-the-federation.md)
<!-- pagination:end -->
