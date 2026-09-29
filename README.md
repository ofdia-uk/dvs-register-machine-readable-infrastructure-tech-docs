> [!CAUTION]
> **Work in progress**
>
> This documentation is a work in progress and is subject to change.

# DVS register machine-readable infrastructure technical documentation

The DVS register machine-readable infrastructure lets certified DVS providers show what they're certified to do to other DVS providers and to public authorities.

It gives you signed information that you can check and store. You can use it to confirm the scope of another provider's certification without looking them up on the register each time.

The Office for Digital Identities and Attributes (OfDIA) runs the machine-readable infrastructure.

> [!NOTE]
> We're still designing parts of the machine-readable infrastructure. This documentation describes our current approach so that you can start planning your integration.
>
> Some details, such as cache durations and validity periods, will follow. We'll update this documentation as we confirm them. You can [see what's still to be confirmed](docs/information-to-follow.md).

## Who this documentation is for

This documentation is for developers, architects and product managers working for:

- certified DVS providers on the [register of digital identity and attribute services](https://www.digital-identity-services-register.service.gov.uk/)
- [public authorities](docs/public-authorities.md) that need to check a DVS provider's certification

It will help you to:

- understand [how trust works in the DVS register machine-readable infrastructure](docs/how-trust-works.md)
- [join the DVS register federation](docs/join-the-federation.md)
- plan how you'll [check other providers' certification](docs/check-another-provider.md)

## How the machine-readable infrastructure works

The machine-readable infrastructure is made up of 3 parts:

- a private public key infrastructure (PKI), which lets participants authenticate when they use the  machine-readable infrastructure's APIs
- an [OpenID Federation](https://openid.net/specs/openid-federation-1_1.html), which lets DVS providers share the scope of their certification
- a verified issuer certificate authority list (VICAL) and a reader identity certificate authority list (RICAL), which support checks when a credential is presented in person, including offline

The machine-readable infrastructure is designed so that you can check and cache what it publishes, rather than looking up the register every time you need to check a provider.

You'll set up your participation through a GOV.UK web portal. In this documentation, we call it 'the provider portal'.

## Plan your integration

If you're a DVS provider you should plan to:

1. [Get your transport and signing certificates](docs/get-your-certificates.md) through the portal.
2. [Choose how you'll authenticate](docs/get-your-certificates.md#choose-how-you-authenticate) to the register's APIs – using mutual TLS (mTLS) or `private_key_jwt`.
3. [Choose your entity identifier and create your federation entity keys](docs/join-the-federation.md).
4. [Onboard to the federation](docs/join-the-federation.md#onboard-to-the-federation) through the provider portal.
5. [Publish your entity configuration](docs/join-the-federation.md#publish-your-entity-configuration), including [your trust marks](docs/trust-marks.md).
6. [Onboard to the VICAL or RICAL](docs/vical-and-rical.md), if you issue or read credentials that are presented in person.
7. [Build how you'll check and cache other providers' certification](docs/check-another-provider.md).

If you're a public authority, read the [information for public authorities](docs/public-authorities.md).

## Standards we use

The machine-readable DVS register uses:

- [OpenID Federation 1.1](https://openid.net/specs/openid-federation-1_1.html)
- [ISO/IEC 18013-5:2021](https://www.iso.org/standard/69084.html), for the VICAL
- the draft second edition of ISO/IEC 18013-5 ([ISO/IEC DIS 18013-5](https://www.iso.org/standard/91081.html)), for the RICAL – ISO has not published this edition yet
- mutual TLS (mTLS) client authentication, as defined in [RFC 8705](https://www.rfc-editor.org/rfc/rfc8705), for authenticating to the register's APIs
- `private_key_jwt`, as defined in [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html#ClientAuthentication), for authenticating to the register's APIs

## Contact us

If you have a question about the DVS register machine-readable infrastructure, or feedback on this documentation, email digital.identity.register@dsit.gov.uk.

<!-- pagination:start -->

---

- Next: [How trust works in the machine-readable DVS register](docs/how-trust-works.md)
<!-- pagination:end -->
