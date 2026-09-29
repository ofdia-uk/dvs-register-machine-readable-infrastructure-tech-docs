> [!CAUTION]
> **Work in progress**
>
> This documentation is a work in progress and is subject to change.

# Onboard to the VICAL and RICAL

We plan to publish a verified issuer certificate authority list (VICAL) and a reader identity certificate authority list (RICAL). These will support credentials that are presented in person (proximity presentation), including offline.

The VICAL and RICAL are for credentials in the mdoc format defined in [ISO/IEC 18013-5](https://www.iso.org/standard/69084.html), such as mobile driving licences.

## What the VICAL and RICAL are

The VICAL is a signed list of the certificate authority (CA) certificates of trusted credential issuers. A reader uses it to check that a credential was issued by a trusted issuer. The VICAL is described in Annex C of [ISO/IEC 18013-5:2021](https://www.iso.org/standard/69084.html).

The RICAL is a signed list of the CA certificates of trusted readers. A holder's wallet uses it to check that a reader requesting a credential is trusted. The RICAL is defined in Annex F of the draft second edition of ISO/IEC 18013-5 ([ISO/IEC DIS 18013-5](https://www.iso.org/standard/91081.html)). ISO has not published this edition yet, so details may change.

You can download and store both lists in advance. This means you can use them to verify credentials without connecting to the machine-readable DVS register at the time of presentation.

## Decide which list to onboard to

You should onboard to:

- the VICAL, if you issue credentials that holders present in person
- the RICAL, if you read credentials that holders present in person

If you do both, you should onboard to both lists.

## Onboard through the portal

You'll onboard to the VICAL and RICAL through the portal.

> [!NOTE]
> **Information to follow**
>
> We'll publish how to onboard to the VICAL and RICAL, including:
>
> - the requirements for the CA certificates you'll provide, including where those certificates should come from
> - what other information you'll need to provide in the portal
> - which credential types each list will cover

## Use the VICAL and RICAL

You should use:

- the VICAL, if you read credentials presented in person, to check the issuer of a credential
- the RICAL, if you provide a wallet, to check the reader requesting a credential

To use either list, you should:

1. Download the current version of the list.
2. Verify the list's signature.
3. Store the list, so it's available when you verify a credential offline.
4. Download and verify a new version regularly, so your stored list stays up to date.

When you verify a credential offline, any revocation information you use is only as up to date as the last time you downloaded it.

> [!NOTE]
> **Information to follow**
>
> We'll publish:
>
> - which edition of ISO/IEC 18013-5 the VICAL and RICAL will follow, and any profile we'll apply to them
> - where you can download the VICAL and RICAL
> - how to verify the signature on each list, including which certificates to trust
> - how often we'll update each list
> - how long each version of a list will be valid for, and how often you should check for a new version
> - how you can link an issuer's CA certificate in the VICAL to that provider's certification in the federation

<!-- pagination:start -->

---

- Previous: [Understand trust marks](trust-marks.md)
- Next: [Check another provider's certification](check-another-provider.md)
<!-- pagination:end -->
