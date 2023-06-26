# Interview Red Flags
## Or . . . Things Seen in the Wild So You Don't Have To

## Contents

## Obvious "No"

### Cucumber/Gherkin

This forces step functions, connecting logic, and not-really-readable-English to live in different places. Which is especially galling because PMs never read (and really never ever write) those tests . . . the whole reason this shit exists!

### Postman/SoapUI/etc.

First, why any of those instead of curl?

Second, as an owner of CI, I just want actual code checked in. As a manager, I want code review to be easy and use standard tooling. These gimmicky test platforms don't do that.

### Selenium

Selenium is based on WebDriver, just like Puppeteer, WebDriverIO, Protractor, and many others.

There are many reasons almost all Angular devs don't use Protractor anymore (slow, brittle, maintenance time, hard to debug) and they now use Cypress . . .

And that (plus Grid and More) is why I don't want Selenium ever again.

### Java

Most of the worst code I've seen is in Java. It has too many features and too many foot-guns. And it encourages complexity, not simplicity.

### End-to-End Only
