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
  - [2.8. Performance](#28-performance)
  - [2.9. Security](#29-security)
  - [2.10. Visual](#210-visual)





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

### 2.2. Compliance

(what regs? STIG?)

### 2.3. Documentation

### 2.4. Failover/Recovery

### 2.5. Install/Upgrade/Uninstall

### 2.6. Localization/Internationalization

### 2.7. Load/Performance/Availability

(leak, drip, volume)

### 2.8. Performance

### 2.9. Security

### 2.10. Visual
