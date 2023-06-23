# On SDETs
## Or . . . Can We Ever Recover from Test Winter?


## Contents
- [1. Origins](#1-origins)
  - [1.1. Old Status Quo](#11-old-status-quo)
  - [1.2. Innovation](#12-Innovation)
  - [1.3. More Hope: Ruby](#13-More-Hope-Ruby)
- [2. Test Winter](#2-test-winter)
  - [2.1. More Automated Manual Tests](#21-more-automated-manual-tests)
  - [2.2. Ruby Abandonment Begins](#22-ruby-abandonment-begins)
  - [2.3. Winter Summary](#23-winter-summary)
- [3. And So It Goes](#3-and-so-it-goes)


## 1. Origins

### 1.1. Old Status Quo

Testing when it was done, was done in larger, traditional companies. It was very little, very slow, very manual scripted testing. Then as now, the less technical the workers are, the more technical language and process they invent.

Another aspect of this kind of testing was magical thinking. There was often the idea that testers were special people with a knack for finding problems and that some people just had a sense for the entire system, that that sense was what we should count on to determine quality.

### 1.2. Innovation

Microsoft invented SDETs and program managers in the late 1990s.

Software Design Engineers in Test were devs who focused on testing. Typically somewhat lower-level devs at the time because veteran SDEs were not likely to switch to SDET. The intent was to have them be parallel tracks, but because of the SDEs tending to be higher level and higher paid, good SDETs often switched to SDE. Thus the caste system of dev over test was reimplemented in the new designation.

SDETs back then were hungry to find ways to apply dev chops to testing, to find ways to inject testing into development practices, and we read and talked broadly about engineering and quality. Favorites included Edwards Deming and Jerry Weinberg. And everyone know about concepts like the [test pyramid](https://martinfowler.com/articles/practical-test-pyramid.html) and we all tried to shift left . . . in some ways I'm still trying to teach people today the same lessons I learned decades ago!

There were also Software Test Engineers, who did more manual testing than SDETs, were generally seen as less technical, and whose automation was mainly UI automation, typically end-to-end. Don't think that the SDETs were the only ones studying. STEs did plenty of that, too.

Microsoft's SDET culture had a big influence on test early at Google and at lots of startups in Seattle and in the Bay area, where Microsoft engineering campuses existed.

### 1.3. More Hope: Ruby

Meanwhile, the Ruby community was thriving. Ruby on Rails was popular. More important to me, though, the Ruby community had innovations in testing. RSpec was the first spec-style BDD framework (BDD without all of the boilerplate; made for devs, not PMs). Ruby's access to S-Expressions at runtime meant it was easy to write tools to introspect and mutate - easy code coverage, static analysis tools, mutation testing and more. And Ruby's friendliness to metaprogramming meant that DSLs abounded for everything, including different test tasks. The mid-to-late 00s were a golden age of test dev work in Ruby - the best language ever for testing.



## 2. Test Winter

Sometime in the late 00s, a lot of startups decided to "innovate" by having developers do all of the testing, jettisoning testers altogether. I applauded much of this and even helped one company move testing into development. Most test teams were not SDETs and testing was often the slow thing that all happened after dev work was done, slowing down feedback and releases. SDETs in many places (including Microsoft) were invited to apply for dev roles or leave.

It also meant that orgs lost whatever testing knowledge they might have had previously. The shallow knowledge was transferred, sometimes lossily (test doubles being one example of lossy transfer - many people call them all mocks now). Unit tests continued. Sometimes rough perf tests. And because everyone discovered that something was missing but the test pyramid was lost knowledge. The obvious next thing to add was end-to-end testing - just like the bad manual scripted testing, but automated.

### 2.1. More Automated Manual Tests

Meanwhile, the orgs that had been stuck doing old, slow manual scripted tests needed to innovate, too. They would go faster by automating! Automating what and how? Automating the exact steps that their manual scripted tests followed, of course.

[That](https://medium.com/slalom-build/dont-automate-test-cases-58e3b959ce6) is a bad idea. As [more than one person](https://www.accelq.com/blog/dont-use-manual-test-cases-for-automation/) will tell you.

> Automating My Walk to the Library
>
>My own explanation is by way of my visiting the library. Every week, at least once a week, I go to my local public library. I either walk or take a car. On foot, my route is along the edge of a park and near certain houses where I really like their plantings. It's also a fairly direct route. In a car, I travel according to where the least stoplights/signs exist and I take a more circuitous route and plan to drive by potential parking spaces. Driving through the park would be more difficult and it would take me on a route with much less parking available unless I want to pay for expensive ramp parking.
>
>Driving is faster. It automates "going to the library," but does not automate the exact steps that I take when I manually (pedally?) go to the library.
>
>Similarly, test automation pays attention to how the code is structured, not the human experience. As it should. When we automate, we should focus on fully exercising the code, not on trying to be simulated humans. Ideally, we'll do as much of that testing without touching UI because UI is intended as a lossy interface that humans can "figure out," whereas APIs are intended to be used by mechanical processes. (Actually the UI paradigm we've had for the last several decades is based on the interface Xerox PARC designed to be discoverable for children, as [Doug Engelbart explains in The Mother of All Demos](https://invention.si.edu/mother-all-demos).)

### 2.2. Ruby Abandonment Begins

And again, meanwhile, RoR lost its shine. People started looking at SOA (later microservices) and things like React on the front end. And Ruby for non-Rails use started slipping, too, Python gaining over it because of emerging ML/data science coding. Python does not have a test culture like Ruby had. Honestly, I don't think any language community does - bits of JS/TS or Scala, but nothing like Ruby.

### 2.3. Winter Summary

So by the end of test winter, we had unit tests and end-to-end tests and not much else.

This lack of knowledge and lack of testing in the middle of the pyramid meant a return to magical thinking about testing. It wasn't anything that we could measure in a meaningful way, so we hoped that testers had the special sense for bug-finding.

Also, those people hired to do end-to-end UI automation, mimicking scripted manual tests were being called SDETs. This was shocking. They weren't recommending all of the faster tests that would cover error paths. They often weren't even measuring code coverage to see what code paths they missed entirely. At the turn of the millennium at Microsoft, people doing this would have been STEs, not SDETs. I don't think it's just another case of title inflation (like how the skill set that used to be senior engineer a decade or two ago is staff or even principal engineer now).



## 3. And So It Goes

Is winter over? I'm not so sure. In a world where most SDETs code Java/Selenium/Cucumber? In a world where devs decide that "strong typing" (by which they actually mean "static typing" - Ruby, for instance is dynamically and strongly typed) means they don't have to write unit tests? In a world where I seem like a pariah because I claim the most important thing for tests to be is fast?

I am starting to hear other people talk about contract tests. That gives me hope. Contract tests and component/service tests should be the vast majority of tests after unit tests. They're fast, low maintenance, and easy to debug. Not to mention that they make 100% code coverage trivially easy.

The biggest obstacle seems to be superstition, given that rigorous testing barely exists anywhere so people rely on magical thinking.
