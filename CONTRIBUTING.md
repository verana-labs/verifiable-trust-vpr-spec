# Contributing to the Verifiable Public Registry specification

This file records how the draft specification ([spec.md](spec.md)) is written
and checked. Follow it for every change, so that reviews deal with content and
not with form.

## Before you push

Run the checks:

```
npm install
npm run check
```

`npm run check` builds the HTML and then runs
[scripts/check-spec.mjs](scripts/check-spec.mjs). The script fails when:

- an internal link points to an anchor that does not exist;
- a link to the [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
  points to an anchor that does not exist there;
- the glossary is not in alphabetical order, defines a term twice, lacks a
  definition for a referenced term, or defines a term that nothing references;
- the text cites a rule id, such as `[AUTHZ-CHECK-5]`, that neither
  specification defines.

The links to the Verifiable Trust specification are checked only when that
repository is cloned next to this one, as `../verifiable-trust-spec`, and built
there. Do that whenever a change renames a heading, a message, a field or an
enumeration value: the Verifiable Trust specification links to this one in
many places, and a renamed heading breaks those links without any build error.
Run `npm run check` in that repository too.

## Writing rules

### Normative and non-normative text

- A requirement appears once, in a normative section, under a rule id.
- Non-normative text (overviews, notes, examples, sections marked
  *non-normative*) names the concept and cites the rule id. It does not use
  MUST, SHOULD or MAY, does not explain the values of an enumeration, and does
  not state conformance levels. If an overview needs a requirement to make
  sense, link to the rule instead of restating it.

### Glossary

- An entry says what the term means, in one or two sentences, with at most one
  link. Rules, lists of values and procedures belong in the normative sections.
- Entries are in alphabetical order.
- Every entry is referenced at least once with `[[ref: term]]`. Remove an entry
  when its last reference goes.
- A term has one spelling. Add an alias to the `[[def: term, alias]]` line only
  when the text needs it.

### Section ids, messages and `MsgType`

- A section id such as `[MOD-AC-MSG-10]` is stable. When a message or a query
  is removed, its section stays with the title `Void`, so that the other ids
  do not move.
- A link to a message section uses the anchor of its heading. Renaming a
  message changes that anchor: update every link here and in the Verifiable
  Trust specification.
- Until a version is released, the values of `MsgType` may be renumbered to
  stay contiguous. After the release they are fixed.

### State

- No redundancy: the state stores no field that can be derived from another
  field.

### Data model diagram

- Draw each enumeration as a relation. Do not declare it as an attribute of an
  entity.
- Do not list an attribute in an entity when a relationship line already shows
  it.

### Vocabulary

Use the terms of the glossary. In particular:

| Write | Do not write |
| --- | --- |
| a participant that holds a grantor accreditation | ecosystem operator |
| accreditation, accreditation entry | permission, or participant as the name of the entry |
| onboarding process | validation process |
| exclusion, excluded | blacklist, blacklisted |
| credential exchange, exchange record | session |
| trust resolution reads the registry through an indexer | queries the registry API in real time |

`PERMISSIONLESS` and `OPEN` are different values. Under `PERMISSIONLESS` a
holder needs no entry in the registry. Under `OPEN` a participant creates its
own entry.

## Commits and pull requests

- One change per commit.
- Do not name customers or prospects in commits, pull requests or issues.
  Describe the role instead.
- The description of the pull request that carries a new version is a summary,
  by theme, of the differences from the previous version. It is not a commit
  log. When a change lands, edit the bullet it affects.
- A pull request that changes a frozen version needs a review from an owner of
  that path. See [README.md](README.md).
