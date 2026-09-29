> [!CAUTION]
> **Work in progress**
>
> This documentation is a work in progress and is subject to change.

# Information to follow

We're still designing parts of the machine-readable infrastructure for the DVS register. This page lists the information we have not published yet, so you can plan around it.

We'll update this documentation as we confirm each item. You can check the repository's [commit history](https://github.com/ofdia-uk/machine-readable-register-tech-docs/commits/main/) to see what's changed.

If you have views on any of these items, [contact us](../README.md#contact-us).
## General

We'll publish:

- when each part of the machine-readable DVS register will be available
- details of any test environment
- which certificates to trust for TLS connections to the register's endpoints

## Certificates

We'll publish:

- how to get access to the portal
- step-by-step instructions for generating your transport and signing certificates
- any other key and certificate requirements, beyond the [supported key types](get-your-certificates.md#generate-your-certificates)
- what information your certificates will contain
- how long your certificates will be valid for, and how to renew them
- when certificates will be revoked, and what to do if you think a private key has been compromised
- the locations of the OCSP responder and the certificate revocation lists (CRLs)

Find out more about [getting your certificates](get-your-certificates.md).

## Authentication

We'll publish:

- which of the register's APIs you'll use your certificates for
- which of those APIs accept mTLS and which accept `private_key_jwt`
- how you'll be identified when you authenticate, such as a client identifier

You do not need to authenticate to use the federation's endpoints.

Find out more about [choosing how you authenticate](get-your-certificates.md#choose-how-you-authenticate).

## Joining the federation

We'll publish:

- the entity identifier of the OfDIA trust anchor
- how to get the trust anchor's public keys securely
- the entity identifier of the federation intermediate
- whether you should have one entity identifier for your organisation, or one for each of your registered services
- which key types and signing algorithms the federation supports
- how to onboard to the federation, including what information you'll need to provide in the portal
- which entity types and metadata you should include in your entity configuration
- how long your entity configuration should be valid for
- how to update the federation public keys that the federation intermediate holds for you when you rotate your keys
- what to do if you think one of your federation private keys has been compromised

Find out more about [joining the federation](join-the-federation.md).

## Trust marks

We'll publish:

- the list of trust mark type identifiers
- OfDIA's trust mark issuer entity identifier
- how long trust marks will be valid for
- whether trust marks will contain any other claims
- how you'll receive your trust marks, including when your certification changes
- the location of the trust mark status endpoint
- how trust marks will show which of your services a certification applies to, if you have more than one service
- how trust marks will show which version of the trust framework you're certified against, while services move from version 0.4 to version 1.0
- how changes to your certification, such as a suspension or withdrawal, will show in the trust mark status endpoint, and how quickly

Find out more about [trust marks](trust-marks.md).

## Checking another provider's certification

We'll publish:

- how you'll match a DVS provider's entry on the register of digital identity and attribute services to its entity identifier
- whether the federation intermediate's list endpoint will support filtering by trust mark type
- recommended cache durations for each artefact
- how long each artefact will be valid for
- how quickly a change to a provider's certification will be reflected in the artefacts
- whether the federation intermediate will set metadata, metadata policies or constraints in its subordinate statements
- the location of the resolve endpoint
- which entity signs resolve responses, and how to get its keys

Find out more about [checking another provider's certification](check-another-provider.md).

## VICAL and RICAL

We'll publish:

- the requirements for the certificate authority (CA) certificates you'll provide, including where those certificates should come from
- what other information you'll need to provide in the portal
- which credential types each list will cover
- how you can link an issuer's CA certificate in the VICAL to that provider's certification in the federation
- which edition of ISO/IEC 18013-5 the VICAL and RICAL will follow, and any profile we'll apply to them
- where you can download the VICAL and RICAL
- how to verify the signature on each list, including which certificates to trust
- how often we'll update each list
- how long each version of a list will be valid for, and how often you should check for a new version

Find out more about [the VICAL and RICAL](vical-and-rical.md).

## Public authorities

We'll share more about how public authorities will take part, including:

- how public authorities will get access to the machine-readable DVS register
- what public authorities will need to set up
- how public authorities will check a DVS provider's certification

Find out more in the [information for public authorities](public-authorities.md).

<!-- pagination:start -->

---

- Previous: [Information for public authorities](public-authorities.md)
- Next: [Glossary](glossary.md)
<!-- pagination:end -->
