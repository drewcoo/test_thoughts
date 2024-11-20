# Testing the Infrastructure

## Contents
- [1. Purpose](#1-purpose)
- [2. Packaging](#2-packaging)  
- [3. Deployment](#3-deployment)
- [4. Cloud](#4-cloud)
  - [4.1. OPA](#41-opa)
- [5. Kubernetes](#5-kubernetes)
  - [5.1. Sonobuoy](#51-sonobuoy)
  - [5.2. Datree](#52-datree)
- [6. Automated Reasoning](#6-automated-reasoning)
- [7. General Infra Testing](#7-general-infra-testing)

## 1. Purpose

Lately a surprising number of people have said to me "but we're testing infrastructure, so what you've said doesn't apply."

First, everything else generally applies. You might have to squint to see how deployed infra is like a service, but it all applies.

Second, there are some specialized tools and techniques, so this doc will cover that.

## 2. Packaging

### 2.1. SBOM

https://www.ntia.gov/files/ntia/publications/sbom_faq_-_20201116.pdf

https://docs.snyk.io/snyk-cli/commands/sbom

## 3. Deployment

There should be post-deployment behavioral tests and there may be additional perf tests, too.

## 4. Cloud

### 4.1. OPA

https://www.openpolicyagent.org

#### 4.1.1. Conftest

Policy testing in Rego language.

https://www.conftest.dev



## 5. Kubernetes

### 5.1. Sonobuoy

https://sonobuoy.io

### 5.2. Datree

https://hub.datree.io/welcome/how-datree-works

## 6. Automated Reasoning

https://aws.amazon.com/blogs/security/an-unexpected-discovery-automated-reasoning-often-makes-systems-more-efficient-and-easier-to-maintain/


## 7. General Infra Testing

https://testinfra.readthedocs.io/en/latest/


Combine this with [pspec](https://pypi.org/project/pytest-pspec/) on [PyTest](https://docs.pytest.org/en/stable/) and you have BDD-style tests.
