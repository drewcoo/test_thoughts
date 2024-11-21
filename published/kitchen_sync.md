# The Kitchen Sync: Often-asked Test Sync Questions

## Contents
- [1. Purpose](#1-purpose)
  - [1.1. No Best Practices](#11-no-best-practices)
- [2. Docs](#2-docs)
  - [2.1. Literate Programming](#21-literate-programming)
  - [2.2. The Tests Are the Docs](#22-the-tests-are-the-docs)
  - [2.3. Keep Docs in Source Control](#23-keep-docs-in-source-control)
- [3. Tests](#3-tests)

- [4. Test Data](#4-test-data)
  - [4.1. Version Hell](#41-version-hell)
  - [4.2. Bad (Anti-Testable) Prod Design](#42-bad-anti-testable-prod-design)


## 1. Purpose

I've often been asked questions about these or had these activities demanded. They roughly clump together, but are a [kitchen sink](https://www.merriam-webster.com/dictionary/kitchen-sink) of synchronization issues.

### 1.1. No Best Practices

I still consider myself a [context-driven tester](https://context-driven-testing.com) and as such don't believe in best practices. These are just different practices and my opinions about them. I hope it generates discussion.

## 2. Docs

There is a common blaming and shaming around remembering to update docs. Docs should be kept in sync with the current state of the code. Older versions can be kept in version control for history. We can add sections to the docs for potential future plans, but shouldn't have docs describe only unrealized futures - that puts them out of sync, too.

### 2.1. Literate Programming

[Literate programming](https://en.wikipedia.org/wiki/Literate_programming) seems like a great idea until you try it and realize it's really a lot more work than just updating a document.

### 2.2. The Tests Are the Docs

This can happen more often than literate programming and [it's lovely when it works but unit tests tend to not be complete enough to describe how code works](https://technologyconversations.com/2014/04/08/tests-as-documentation/). Especially in these days where people substitute type checking for behavioral tests.

Though I'm skeptical of claims this will work, I think well-written BDD-style tests can be self-documenting and also fully document the behaviors tested. And on this topic, I'm a huge fan of spec-style BDD (started with [RSpec](https://rspec.info), now wider-spread in places such as [Cypress](https://www.cypress.io) or [pspec](https://pypi.org/project/pytest-pspec/)(used with PyTest)). It has all the benefits of [Cucumber](https://cucumber.io)/[Gherkin](https://cucumber.io/docs/gherkin/) with less maintenance/overhead/possible-bugs.

## 2.3. Keep Docs in Source Control

This is wonderful for finding docs relevant to code. It also allows code reviewers to say "I like the code changes, but the docs were not updated," or possibly using commit hooks to send reminders, giving process/team a chance to help keep docs up to date. [Markdown](https://www.markdownguide.org) is great for this - decent markup plus easy-to-review source diffs (and [Mermaid](https://mermaid.js.org) for embedding PlantUML-like graphs inline).

Unfortunately, it's hard to tell where docs go when they don't relate directly to a particular project. Part of this problem are docs that apply to multiple projects - one of the several things that are needed x-project and make me a fan of monorepos (and docs at the level of the hierarchy where they are most applicable).

## 3. Tests

People seem to also struggle keeping their tests in sync with the dev code.

### 3.1. Run Often

A running test is in sync with the code it is testing.

#### 3.1.1. Code Coverage

Use code coverage to determine if new dev functionality has been added that's not covered by test code yet.

#### 3.1.1. Run in CI on Commit

If you run service/contract tests against every (relevant) commit, your code will always be in sync.

Running end-to-end (E2E) tests in an environment makes it more difficult to stay in sync. The tests themselves are more complex and longer-running than service-level ones. The environments tend to be fiddly, too. Often there are limited environments. Over all, these factors generally mean that E2E tests are not run on every commit, so they are more likely out of sync (and also more difficult to diagnose and fix when they fail). If you absolutely have to run end-to-end tests, try to do it in ephemeral environments, spun up into a known state just for your tests - that's more stable/reliable and often can be lightweight enough to allow some E2E tests to run more frequently and stay in sync better.

## 4. Test Data

I've been asked how I handle test many times and every time it comes from an interlocutor experiencing one or both of two anti-patterns:

### 4.1. Version Hell

There are lots of repos and from them spring many pieces of software (prod or test) that need to interoperate. But what versions of which are supposed to (or have been tested to prove they) work together? And how do you gently version-caress data to work in that soup, too?

I strongly recommend monorepos for this. The many-repo pattern started when it became cheap/easy to create repos on Github. There are many concerns (docs, testing, ops) that touch more than one project, so it makes sense to put the projects in the same versioning-space.

### 4.2. Bad (Anti-Testable) Prod Design

More often this shows itself by demands to be good at writing complex SQL queries, but sometimes it occurs as questions about data management. These are signs of faulty, untestable prod code.

The reaction to this assertion is that the prod code works fine. Great, how can someone prove it? (Answer: simple tests.) [Testability](https://en.wikipedia.org/wiki/Software_testability) is about being able to know and set internal conditions, to decompose systems, and reason about them.
