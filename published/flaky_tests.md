# Flaky Tests

## Contents
- [1. Purpose](#1-purpose)
  - [1.1. Define Flaky Tests](#11-define-flaky-tests)
  - [1.2. Rerun Until Pass](#12-rerun-until-pass)
  - [1.3. A Better Way](#13-a-better-way)
- [2. Causes and Mitigations](#2-causes-and-mitigations)
  - [2.1. Collisions and Defensive Coding](#21-collisions-and-defensive-coding)
  - [2.2. Large Tests and Decomposition](#22-large-tests-and-decomposition)
  - [2.3. General: Temporary Removal](#23-general-temporary-removal)


## 1. Purpose

### 1.1. Define Flaky Tests

Flaky (or sometimes "flapping" or other terms) tests are tests that sometimes pass and sometimes fail, for currently unknown reasons.

### 1.2. Rerun Until Pass

There are many shops where flaky tests are run again until they pass. This doesn't tell us why they failed. This also makes test runs take longer. There must be a better way!

### 1.3. A Better Way

The purpose of this doc is to discuss better ways. Ideally, ways to avoid flaky tests altogether.

Contrary to [people making a product to deal with flaky tests](https://trunk.io/blog/what-we-learned-from-analyzing-20-2-million-ci-jobs-in-trunk-flaky-tests-part-1#you-will-always-have-some-flaky-tests), you do not need to have flaky tests.

## 2. Causes and Mitigations

The following causes and their mitigations are orthogonal with one another, none of them are mutually exclusive.

|Cause|Symptoms|Mitigation|
|---|---|---|
|Data Collisions|Reused Data in Test Cases (Even Across Test Runs with Same Environment)|[Defensive Coding](#21-collisions-and-defensive-coding)|
|Large Tests|End-to-End tests in a Full Environment|[Decomposition](#22-large-tests-and-decomposition)|
|General|Can Be Used with Any Cause|[Temporary Removal](#23-general-temporary-removal)|

### 2.1. Collisions and Defensive Coding

One cause for flaky tests is tests that are not independent. If several tests run against the same instance of a system, creating random independent data can avoid collisions (recommend: UUIDs).

Running tests in random order can detect some of these problems sometimes. This introduces short-term flakiness while problems are found and fixed, but guards against long-term flakiness.

> Good use of randomization can also be useful in having "tests that test themselves." We typically form [equivalence class partitions](https://en.wikipedia.org/wiki/Equivalence_partitioning) and randomly sampling data "in the middle" of the partition in addition to testing boundary values can help us guarantee that data is partitioned correctly.

## 2.2. Large Tests and Decomposition

Large (often End-to-End) tests requiring many running services and possibly a full environment can be flaky because of the raw number of unconstrained variables. Decomposing those tests into smaller pieces that run against less production code can help.

With the exception of monoliths, we can usually break our environment into several services (isolated service-level tests) and the interfaces between them ([contract tests](https://pact.io)). This can allow us to trivially reach 100% code coverage (no more hard-to-reach error paths!).

## 2.3. General: Temporary Removal

We can remove the tests (or mark as skipped), file a bug to fix the tests, and comment the bug number in the test code.

This means all active tests should be expected to pass in every run.

All deactivated tests are still tracked and we should expect their fixes to be scheduled for future iterations.
