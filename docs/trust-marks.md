> [!CAUTION]
> **Work in progress**
>
> This documentation is a work in progress and is subject to change.

# Understand trust marks

In OpenID Federation, a trust mark is a signed statement that an entity meets a defined set of requirements.

OfDIA issues trust marks to DVS providers to show the scope of their certification. You include your trust marks in your entity configuration, so other participants can check what you're certified to do.

> [!NOTE]
> Federation trust marks are machine-readable statements. They're not the same as the UK CertifID trust mark.

## What OfDIA issues

OfDIA issues a separate trust mark for each part of a digital verification services certification, such as:

- each role it is certified to perform
- each identity profile it is certified against
- each supplementary code it is certified against

Each trust mark has a trust mark type identifier. This shows which part of your certification the trust mark represents.

OpenID Federation 1.1 requires trust mark type identifiers to be unique across federations, and recommends that each one is based on a URL for the federation or trust framework.

> [!NOTE]
> **Information to follow**
>
> We'll publish:
>
> - the list of trust mark type identifiers
> - how trust marks will show which of your services a certification applies to, if you have more than one service
> - how trust marks will show which version of the trust framework you're certified against, while services move from version 0.4 to version 1.0

## What a trust mark contains

A trust mark is a signed JWT with its `typ` header set to `trust-mark+jwt`. OfDIA's trust mark issuer signs it with one of its federation entity keys, and sets the `kid` header to the ID of that key.

OfDIA's trust mark issuer is an entity in the federation. The OfDIA trust anchor lists it in the `trust_mark_issuers` claim of its entity configuration, to show which trust mark types it's trusted to issue.

A trust mark's claims include:

| Claim | Value |
| --- | --- |
| `iss` | The entity identifier of OfDIA's trust mark issuer |
| `sub` | Your entity identifier |
| `trust_mark_type` | The trust mark type identifier |
| `iat` | The time OfDIA issued the trust mark, as a number of seconds since the Unix epoch |
| `exp` | The time the trust mark expires, as a number of seconds since the Unix epoch – a trust mark without `exp` does not expire |

See [section 7 of OpenID Federation 1.1](https://openid.net/specs/openid-federation-1_1.html#name-trust-marks) for the full definition of a trust mark.

> [!NOTE]
> **Information to follow**
>
> We'll confirm:
>
> - OfDIA's trust mark issuer entity identifier
> - how long trust marks will be valid for
> - whether trust marks will contain any other claims

## Get your trust marks

OfDIA will issue your trust marks based on your certification.

> [!NOTE]
> **Information to follow**
>
> We'll publish how you'll receive your trust marks, and how you'll receive new trust marks when your certification changes.

## Add your trust marks to your entity configuration

You should add your trust marks to the `trust_marks` claim in your [entity configuration](join-the-federation.md#publish-your-entity-configuration).

The `trust_marks` claim is an array. Each item in the array is an object with these members:

| Member | Value |
| --- | --- |
| `trust_mark_type` | The trust mark type identifier. This must match the `trust_mark_type` claim in the trust mark itself |
| `trust_mark` | The signed trust mark JWT that OfDIA issued to you |

For example:

```json
"trust_marks": [
  {
    "trust_mark_type": "[TRUST MARK TYPE IDENTIFIER]",
    "trust_mark": "[SIGNED TRUST MARK JWT ISSUED BY OFDIA]"
  }
]
```

## When your certification changes

If your certification changes, OfDIA will change the trust marks we issues to you too.

You should publish a new entity configuration when:

- OfDIA issues you with a new trust mark
- one of your trust marks expires or is revoked

You should remove any trust marks that have expired or been revoked from ....

## Check the status of a trust mark

OfDIA will provide a trust mark status endpoint, as described in [section 8.4 of OpenID Federation 1.1](https://openid.net/specs/openid-federation-1_1.html#name-trust-mark-status). Participants can use it to check whether a trust mark is still active.

When the endpoint is available, you'll find its location in the `federation_trust_mark_status_endpoint` parameter of the `federation_entity` metadata in the entity configuration of OfDIA's trust mark issuer.

To check a trust mark's status, send it as the `trust_mark` parameter in a POST request to the endpoint. The endpoint returns a signed JWT with its `typ` header set to `trust-mark-status-response+jwt`. OpenID Federation 1.0 defines these values for its `status` claim:

- `active`
- `expired`
- `revoked`
- `invalid`

You must check the response's `typ` header and signature before you rely on it.

> [!NOTE]
> **Information to follow**
>
> We'll publish:
>
> - the location of the trust mark status endpoint
> - how changes to your certification, such as a suspension or withdrawal, will show in the trust mark status endpoint, and how quickly

Find out how to [check another provider's certification](check-another-provider.md), including how to validate their trust marks.

<!-- pagination:start -->

---

- Previous: [Join the federation](join-the-federation.md)
- Next: [Onboard to the VICAL and RICAL](vical-and-rical.md)
<!-- pagination:end -->
