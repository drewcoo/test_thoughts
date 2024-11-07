# Nonfunctional Testing

## Contents
- [1. Definitions](#1-definitions)
  - [1.1. Functional Testing](#11-functional-testing)
  - [1.2. Nonfunctional Testing](#12-nonfunctional-testing)
- [2. Types](#2-types)
  - [2.1. Accessibility](#21-accessibility)
  - [2.2. Compliance](#22-compliance)
  - [2.3. Documentation](#23-documentation)
  - [2.4. Failover/Recovery](#24-failover-recovery)
  - [2.5. Install/Upgrade/Uninstall](#25-install-upgrade-uninstall)
  - [2.6. Localization/Internationalization](#26-localization-internationalization)
  - [2.7. Load/Performance/Availability](#27-load-performance-availability)
  - [2.8. Security](#28-security)
  - [2.9. Visual](#29-visual)





## 1. Definitions

### 1.1. Functional Testing

A mathematical function is a mapping from one or more domains to one or more ranges.

Functional tests treat software under test as a function or some composition of functions.

The functions can be tested behaviorally (as talked about in [Test Pyramid](./test_pyramid.md))/

The composition of functions is tested by contract testing, also mentioned in [Test Pyramid](./test_pyramid.md).

Sometimes it's also possible to wrap non-functional behaviors in a pseudo-function.

Most stories and specs cover only "happy path," most-used functional activity, so there's a great deal of functional testing that goes beyond those things.

### 1.2. Nonfunctional Testing

Nonfunctional testing, then is testing all of the things that can't be treated as functions.

In functional programming terms, this means testing the side effects. These can include performance characteristics, how humans perceive outputs, and more.

Except for promises about performance or explicit customer requests for things like accessibility and security, nonfunctional tests almost never map to stories or specs.

## 2. Types

This is not meant to be an exhaustive list.

### 2.1. Accessibility

[Accessibility testing](https://www.section508.gov) is especially important for large organizations or government work.

I usually lean heavily on tools like [Axe](https://www.deque.com/axe/). For web UI, there's a [plugin for Cypress](https://www.npmjs.com/package/cypress-axe) and [one for Playwright](https://www.npmjs.com/package/axe-playwright), as examples.

### 2.2. Compliance

Tests here are for compliance with things like [HIPPA](https://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/index.html) and [SOX](https://en.wikipedia.org/wiki/Sarbanes%E2%80%93Oxley_Act).

### 2.3. Documentation

These are to make sure customer-facing docs are correct and procedures work as expected.

### 2.4. Failover/Recovery

When the system stops working, does it automatically fail over?

If there are manual recovery steps, do they work? In the time expected?

### 2.5. Install/Upgrade/Uninstall

Does a clean install work correctly?

What about upgrades/downgrades?

Does an uninstall clean up after itself?

Does a reinstall work?

### 2.6. Localization/Internationalization

For software with an international presence, this is more important.

Do local conventions work (currency, time zones, text, directional text formatting, etc.)?

Also worth considering: [pseudo-localization](https://en.wikipedia.org/wiki/Pseudolocalization) to make sure all the right strings are localized.

### 2.7. Load/Performance/Availability

Also leak, drip, volume, and others.

These test all involve sending a lot of network traffic at a service.

I used to use [JMeter](https://jmeter.apache.org) for this but switched to [k6](https://k6.io) a few years ago because it's easier to understand (and code review) config changes with k6 - JavaScript instead of XML files!

There may be things like SLAs to be tested against.

If not, this covers throughput (and timing) for traffic at scale.

### 2.8. Security

Most commonly, this includes static and dynamic scanning. Static checking can involve code analysis or analysis of dependencies (with a tool like [Snyk](https://snyk.io/code-checker/sbom-security/)). Dynamic can include scanning with things like [Nessus](https://www.tenable.com/products/nessus) and [OWASP ZAP](https://www.zaproxy.org).

For a more in-depth look at security, try [threat modeling](https://owasp.org/www-community/Threat_Modeling) (I prefer [STRIDE](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats) for that).

### 2.9. Visual

Visual testing involves taking snapshots of UI and diffing them with previous known-good snapshots. There are tools to do this with [Cypress](https://docs.cypress.io/app/tooling/visual-testing), [Playwright](https://medium.com/@divyarajsinhdev/visual-comparison-using-playwright-a-comprehensive-guide-7f2f54ba10c3) and other tools.
