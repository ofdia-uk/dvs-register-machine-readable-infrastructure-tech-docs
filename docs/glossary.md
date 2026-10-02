> [!CAUTION]
> **Work in progress**
>
> This documentation is a work in progress and is subject to change.

# Glossary

These are the terms we use in this documentation.

## Certificate authority (CA)

An organisation or system that issues digital certificates. In the machine-readable DVS register, OfDIA operates the root CA.

## Certificate revocation list (CRL)

A signed list of the certificates that a CA has revoked before their expiry date. It's defined in [RFC 5280](https://www.rfc-editor.org/rfc/rfc5280).

## Certificate signing request (CSR)

A request you send to a CA to get a certificate. It contains your public key and the details to include in the certificate. You keep the private key.

## DVS provider

An organisation that provides digital verification services and that is certified and registered against the DVS trust framework.

## Entity

A participant in the federation, such as a DVS provider, the federation intermediate or the OfDIA trust anchor.

## Entity configuration

A signed statement that an entity publishes about itself. It contains the entity's federation public keys, metadata and trust marks. Each entity hosts its entity configuration at its entity identifier followed by `/.well-known/openid-federation`.

## Entity identifier

A URL that identifies an entity in the federation.

## Federation endpoints

Endpoints defined in OpenID Federation 1.0, such as the fetch, list, resolve and trust mark status endpoints. The machine-readable DVS register's federation endpoints are open, so you do not need to authenticate to use them.

## Federation entity keys

The keys an entity uses to sign statements in the federation, such as its entity configuration. They're separate from the transport and signing certificates you get through the portal.

## Federation intermediate

The part of the machine-readable DVS register that publishes subordinate statements about DVS providers. It sits between DVS providers and the OfDIA trust anchor in the trust chain.

## Fetch endpoint

A federation endpoint that returns a subordinate statement about an entity. The trust anchor and the federation intermediate each provide one.

## Holder

The person who the credential or attribute belongs to, who presents it, usually using a digital wallet on their smartphone.

## Issuer

An organisation that issues credentials or attributes to holders.

## JSON Web Key Set (JWKS)

A JSON object that contains a set of public keys. It's defined in [RFC 7517](https://www.rfc-editor.org/rfc/rfc7517).

## JSON Web Token (JWT)

A way of passing claims between systems as a JSON object. The JWTs in this documentation are signed. JWTs are defined in [RFC 7519](https://www.rfc-editor.org/rfc/rfc7519).

## Key ID (kid)

A value that identifies a key in a JWKS. A JWT's `kid` header shows which key was used to sign it.

## List endpoint

A federation endpoint that returns the entity identifiers of an entity's immediate subordinates. The federation intermediate's list endpoint returns the DVS providers in the federation.

## Mdoc

A credential in the format defined in [ISO/IEC 18013-5](https://www.iso.org/standard/69084.html), such as a mobile driving licence. The VICAL and RICAL are for mdoc credentials.

## Metadata policy

Rules in a subordinate statement that change or restrict the metadata of the entity it's about. You apply them when you validate a trust chain, to get the entity's resolved metadata.

## Mutual TLS (mTLS)

A way of authenticating where both sides of a TLS connection present a certificate. You present your transport certificate when you use the register's APIs. mTLS client authentication is defined in [RFC 8705](https://www.rfc-editor.org/rfc/rfc8705).

## Online Certificate Status Protocol (OCSP)

A way to check whether a certificate has been revoked, by asking a service called an OCSP responder. It's defined in [RFC 6960](https://www.rfc-editor.org/rfc/rfc6960).

## OpenID Federation

The [OpenID Federation 1.1](https://openid.net/specs/openid-federation-1_1.html) specification, which the machine-readable DVS register uses to let DVS providers share the scope of their certification.

## private_key_jwt

A way of authenticating where you sign a JSON Web Token (JWT) with your private key and send it as a client assertion. It's defined in [section 9 of OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html#ClientAuthentication). You use the private key for your signing certificate.

## Proximity presentation

When a holder presents a credential in person to a nearby reader. For example, the holder's phone might show a QR code that the reader scans to start a connection. The phone then sends the credential over a short-range connection, such as Bluetooth or NFC.

## Reader

A device or system that requests credentials or attributes from a holder, for example when a credential is presented in person.

## Reader identity certificate authority list (RICAL)

A signed list of the CA certificates of trusted readers. A holder's wallet uses it to check that a reader requesting a credential is trusted. It's defined in Annex F of the draft second edition of ISO/IEC 18013-5.

## Resolve endpoint

An endpoint that returns a provider's resolved metadata, trust marks and trust chain in a single signed response.

## Resolved metadata

An entity's metadata after the metadata and metadata policies in its trust chain have been applied.

## Signing certificate

A certificate you get through the portal. You use it to sign JWTs when you use the register's APIs, such as the client assertion for `private_key_jwt`.

## Subordinate statement

A signed statement that one entity publishes about another entity directly below it in the federation. For example, the federation intermediate publishes a subordinate statement about each DVS provider.

## Transport certificate

A certificate you get through the portal. You use it to authenticate with mTLS when you use the register's APIs.

## Trust anchor

The entity at the top of the federation, which all trust chains end at. OfDIA is the trust anchor.

## Trust chain

A sequence of signed statements that links an entity's entity configuration to the trust anchor.

## Trust mark

A signed statement that an entity meets a defined set of requirements. OfDIA issues a trust mark for each part of a DVS provider's certification.

## Trust mark issuer

An entity in the federation that issues trust marks. OfDIA's trust mark issuer issues trust marks to DVS providers.

## Trust mark status endpoint

A federation endpoint that says whether a trust mark is still active. OfDIA's trust mark issuer provides it.

## Trust mark type identifier

An identifier that shows what a trust mark represents, such as a particular role, identity profile or supplementary code.

## Verified issuer certificate authority list (VICAL)

A signed list of the CA certificates of trusted credential issuers. A reader uses it to check that a credential was issued by a trusted issuer. It's described in Annex C of ISO/IEC 18013-5:2021.

## Wallet

An app that stores a holder's credentials and presents them to readers.

<!-- pagination:start -->

---

- Previous: [Information to follow](information-to-follow.md)
<!-- pagination:end -->
