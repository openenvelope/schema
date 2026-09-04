# Security Policy

## Supported versions

Security fixes are applied to the current `v1` schema. Older major versions remain available for compatibility but may receive only critical security documentation updates.

## Reporting a vulnerability

Please report suspected vulnerabilities privately to **security@openenvelope.org**. Do not open a public issue for an undisclosed vulnerability.

Include, where possible:

- The affected schema field, validator, or consumer behavior
- A minimal example that demonstrates the issue
- The security impact and likely attack path
- Any suggested mitigation

Do not include real credentials, customer data, or other sensitive information in a report or test definition. We aim to acknowledge reports within three business days and will coordinate disclosure after a fix or mitigation is available.

## Scope

This repository defines a data format; it does not execute agents. Reports are in scope when a schema rule or official example can cause unsafe behavior in conforming validators or runtimes. Vulnerabilities in the hosted Envelope product should also be sent to the address above so they can be routed to the correct maintainers.

## Safe harbor

Good-faith research that avoids privacy violations, service disruption, and access to data you do not own is welcome. We will not pursue action against researchers who follow this policy and allow reasonable time for remediation before public disclosure.
