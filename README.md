# Verifiable Public Registry Specification (VPR Spec)

## About

The Verifiable Public Registry Specification describes a decentralized infrastructure — a “registry of trust registries” — used to manage digital trust at scale.

It provides:

- **Trust Registries**: Lists of authorized entities who can issue or verify specific credentials within an Ecosystem.
- **Credential Schema Management**: Defining credential types, their governance, and permissions (who can issue/verify them).
- **Validation Process**: Transparent procedures to authorize issuers, verifiers, and grantors.
- **Tokenized Trust Model**: A mechanism using tokens to reward trustworthy participants, ensure accountability, and prevent misuse.

Its goal is to support open, transparent governance of trust ecosystems and enable global, decentralized identity management.

Browsable spec (latest draft): [https://verana-labs.github.io/verifiable-trust-vpr-spec/](https://verana-labs.github.io/verifiable-trust-vpr-spec/)

Latest stable (v4): [https://verana-labs.github.io/verifiable-trust-vpr-spec/versions/v4/](https://verana-labs.github.io/verifiable-trust-vpr-spec/versions/v4/)

Previous stable (v3): [https://verana-labs.github.io/verifiable-trust-vpr-spec/versions/v3/](https://verana-labs.github.io/verifiable-trust-vpr-spec/versions/v3/)

## Versions

Each version keeps its markdown source in its own directory:

| Version | Source | Page |
| --- | --- | --- |
| v5 (draft) | [spec.md](spec.md) | `/` |
| v4 (stable) | [versions/v4/spec.md](versions/v4/spec.md) | `/versions/v4/` |
| v3 (frozen) | [versions/v3/spec.md](versions/v3/spec.md) | `/versions/v3/` |

CI renders every version from its source on each deploy, so no page can fall
out of step with its markdown.

[.github/CODEOWNERS](.github/CODEOWNERS) lists the frozen versions. A pull
request that changes a frozen version needs a review from an owner of that
path. To freeze a version, add its directory to that file. To unfreeze a
version, delete its line.

The file [index-v3.html](index-v3.html) is not a spec. It redirects the old v3
address to `/versions/v3/`, because other sites link to it. Keep it.

## How to contribute

Clone the repo. Then run `npm install` and `npm run render` to build the HTML.
The render writes one `index.html` for each spec that [specs.json](specs.json) lists.
Git does not track these files. CI builds them again on each deploy.

Contribute by editing [spec.md](spec.md) in a new branch.

To re-render html while you edit the spec.md file, run:

```
npm run dev
```
