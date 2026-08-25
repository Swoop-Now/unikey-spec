# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

The UniKey Technical Specifications — an RFC series defining a decentralized, domain-anchored, pre-execution authorization protocol for AI agents, devices, and payment networks. This is a documentation-only repo: markdown RFCs plus two standalone static HTML pages (`overview.html`, `demo.html`) that open directly in a browser. There is no build, test, or lint tooling.

## Structure

RFCs are numbered by series (defined in `rfc-1000.md`, the master index):

- **1000** — Core & Architecture (1000 index, 1001 Four Primitives, 1200 Delegation, 1300 Device Authority, 1400 Authorization Certificate)
- **2000** — Protocol & Data Formats (2001 Trust Packet Format, 2002 Authorization Ledger, 2003 Scope Grammar & Registry)
- **3000** — Verification & Trust Discovery via DNS/DKIM (3001, 3002)
- **4000** — Conformance & Testing (4001 Compliance Checklist)
- **5000** — Operational Guidance (5003 Authorization Flow, 5004 SMTP Transport Profile)
- **9000** — Informational (reserved)

## Conventions when editing RFCs

- Every RFC opens with a metadata block: Title, Status (Draft/Stable), Category, Version, Date, Authors, Canonical URL — and, for documents migrated from the legacy Swoop Series, a "Previously published as" line.
- On substantive changes, bump the Version and update the Date in the metadata block (see rfc-2001, currently v1.1).
- Three places index the RFC set and must stay in sync when adding, renaming, or changing the status of an RFC: the table in `README.md`, and the Master Index and Migration Map tables in `rfc-1000.md`.
- RFCs cross-reference each other heavily (e.g., 1400 builds on 1001 and 1200; 2002 relates to 1001 and 4001). When changing a concept in one RFC, check the "Relates to" column in rfc-1000's master index for documents that may need matching updates.
- RFC-1400 (Authorization Certificate) is a living document: it stays under active revision until marked Stable, and substantive changes must be recorded in its in-document Change Log.
- Git history shows edits are often driven by external alignment (patent disclosure, threat-model findings, reference implementation); commit messages state which RFCs changed and why.

## Domain framing to preserve

- UniKey is an **authorization** protocol, not an authentication protocol: it proves a specific action was approved through a verifiable authority chain before execution, and explicitly does not verify the legal identity of a person (rfc-1000 §1.3). Keep this distinction intact when editing.
- The suite is fail-closed and zero-trust throughout; security derives from cryptographic proof, not network position.
- The architecture is "four primitives plus one flow": the four cryptographic primitives (rfc-1001) composed by the Authorization Flow Architecture (rfc-5003).
