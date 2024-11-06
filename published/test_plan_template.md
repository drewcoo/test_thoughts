# Test Plan Template

## Contents
- [1. Purpose](#1-Purpose)
  - [1.1. Scope](#11-scope)
  - [1.2. Definitions](#12-definitions)
- [2. Functional Testing](#2-functional-testing)
  - [2.1. Unit](#21-unit)
  - [2.2. App/Service](#22-app-service)
  - [2.3. Contract](#23-contract)
  - [2.4. Deployment](#24-deployment)
  - [2.5 End-to-End](#25-end-to-end)
  - [2.6. Code Coverage](#26-code-coverage)
  - [2.7. Static Analysis](#27-static-analysis)
- [3. Nonfunctional Testing](#3-nonfunctional-testing)
  - [3.1. Accessibility](#31-accessibility)
  - [3.2. Compliance](#32-compliance)
  - [3.3. Documentation](#33-documentation)
  - [3.4. Failover/Recovery](#34-failover-recovery)
  - [3.5. Install/Upgrade/Uninstall](#35-install-upgrade-uninstall)
  - [3.6. Localization/Internationalization](#36-localization-internationalization)
  - [3.7. Load/Performance/Availability](#37-load-performance-availability)
  - [3.8. Security](#38-security)
  - [3.9. Visual](#39-visual)

## 1. Purpose

State the purpose of this testing.

Ideally, link to a dev spec.

### 1.1. Scope

What's in scope? What's out of scope? Call it out here.

### 1.2. Definitions

Are there any definitions a new tester following the plan should know?

## 2. Functional Testing

Ideally, all of this will be automated. If so, don't list test cases here; instead link to source code and also to CI for results. If you're using a BDD framework, the latest test output should be a list of human-readable test cases. (We do this so that test plans don't get out of sync with reality.)

### 2.1. Unit

Ideally devs should do these. Link to the sources and to CI.

These can run on a CI server.

### 2.2. App/Service

This falls on the tester if the unit tests are not sufficient (100% coverage with behavioral tests). Link to sources and to CI.

We can run these tests in isolation on a CI server.

### 2.3. Contract

If there are multiple apps/services involved in this plan, add links to sources and to CI and the management page for contract tests. [Recommend: Pact](https://pact.io) and [PactFlow](https://pactflow.io)

These can also run on a CI server.

### 2.4. Deployment

I started calling "smoke tests" the "deployment tests," instead, because I got tired of explaining smoke tests.

These should be run for a given app/service whenever it's deployed (to production, but ideally anywhere) to make sure that it can talk to anything it normally talks to (like logging and monitoring).

These tests need to be run in an environment, possibly an ephemeral one for pre-production testing.

### 2.5 End-to-End

There should be very, very few of these in today's testing. Ideally none of them. Service and contract and deployment tests should have covered anything here.

Add end-to-end tests here only under duress.

These tests require an environment. Ideally, for pre-production it can be an ephemeral environment but more often these happen in a large, shared, high-maintenance environment.

### 2.6. Code Coverage

We should be measuring [code coverage](https://en.wikipedia.org/wiki/Code_coverage) of functional tests (mainly unit and app/service). If we're doing functional testing as listed here, we should be able to reach 100% coverage easily.

This also means we need to have discussions about the things 100% coverage can't give us. Most of those are in the nonfunctional section. It's worth having a conversation with the devs about possible [race conditions](https://en.wikipedia.org/wiki/Race_condition), making a section for them in this plan and mitigating/preventing them if they exist. Unfortunately, no good general tools exist for finding those yet.

### 2.7. Static Analysis

[Static analysis](https://en.wikipedia.org/wiki/Static_program_analysis) is usually done at build time. I'm mentioning it here because timing- and speed-wise, it's closest to unit or app/service testing.

## 3. Nonfunctional Testing

Ideally, these should also be automated and there should be links to sources, tooling used, and to CI.

### 3.1. Accessibility

[Accessibility testing](https://www.section508.gov) is especially important for large organizations or government work.

I usually lean heavily on tools like [Axe](https://www.deque.com/axe/). For web UI, there's a [plugin for Cypress](https://www.npmjs.com/package/cypress-axe) and [one for Playwright](https://www.npmjs.com/package/axe-playwright), as examples.

### 3.2. Compliance

Tests here are for compliance with things like [HIPPA](https://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/index.html) and [SOX](https://en.wikipedia.org/wiki/Sarbanes%E2%80%93Oxley_Act).

### 3.3. Documentation

These are to make sure customer-facing docs are correct and procedures work as expected.

### 3.4. Failover/Recovery

When the system stops working, does it automatically fail over?

If there are manual recovery steps, do they work? In the time expected?

### 3.5. Install/Upgrade/Uninstall

Does a clean install work correctly?

What about upgrades/downgrades?

Does an uninstall clean up after itself?

Does a reinstall work?

### 3.6. Localization/Internationalization

For software with an international presence, this is more important.

Do local conventions work (currency, time zones, text, directional text formatting, etc.)?

Also worth considering: [pseudo-localization](https://en.wikipedia.org/wiki/Pseudolocalization) to make sure all the right strings are localized.

### 3.7. Load/Performance/Availability

Also leak, drip, volume, and others.

These test all involve sending a lot of network traffic at a service.

I used to use [JMeter](https://jmeter.apache.org) for this but switched to [k6](https://k6.io) a few years ago because it's easier to understand (and code review) config changes with k6 - JavaScript instead of XML files!

There may be things like SLAs to be tested against.

If not, this covers throughput (and timing) for traffic at scale.


### 3.8. Security

Most commonly, this includes static and dynamic scanning. Static checking can involve code analysis or analysis of dependencies (with a tool like [Snyk](https://snyk.io/code-checker/sbom-security/)). Dynamic can include scanning with things like [Nessus](https://www.tenable.com/products/nessus) and [OWASP ZAP](https://www.zaproxy.org).

For a more in-depth look at security, try [threat modeling](https://owasp.org/www-community/Threat_Modeling) (I prefer [STRIDE](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats) for that).

### 3.9. Visual

Visual testing involves taking snapshots of UI and diffing them with previous known-good snapshots. There are tools to do this with [Cypress](https://docs.cypress.io/app/tooling/visual-testing), [Playwright](https://medium.com/@divyarajsinhdev/visual-comparison-using-playwright-a-comprehensive-guide-7f2f54ba10c3) and other tools.
