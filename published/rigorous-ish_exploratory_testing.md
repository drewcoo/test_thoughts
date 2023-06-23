# Rigorous-ish Exploratory Testing

## Contents
- [1. Manual Testing](#1-manual-testing)
  - [1.1. Scripted Manual Testing](#11-scripted-manual-testing)
  - [1.2. Ad Hoc or Guerilla Testing](12-ad-hoc-or-guerilla-testing)
  - [1.3. Exploratory Testing](13-exploratory-testing)
- [2. ET Processes and Artifacts](2-et-processes-and-artifacts)
  - [2.1. Charter](21-charter)
  - [2.2. Briefing](22-briefing)
  - [2.3. Exploration](23-exploration)
    - [2.3.1. Logging](231-logging)
  - [2.4. Debriefing](24-debriefing)



## 1. Manual Testing

Can be UI.

Can be with tools. Things like Postman test APIs, but also CLI tooling can be used to query a system and to tell it what to do.

### 1.1. Scripted Manual Testing

"Scripted" here is in the sense of a script for a play or a movie. Scripted manual testing involves a human manually following prescribed steps.

### 1.2. Ad Hoc or Guerilla Testing

Ad Hoc or Guerilla testing has no pre-arranged steps or goals. Other than finding bugs. Wherever and however you can.

### 1.3. Exploratory Testing

Exploratory testing can look at lot like ad hoc testing, but I prefer something a little more rigorous, where we determine the area of focus and maybe even the methods or approach we'll use.

[James Whittaker likes to use the concept of "tours"](https://www.youtube.com/watch?v=fNkYz1hB7r0) in exploratory testing. Imagine you're a tourist on vacation in a strange city. What kind of tourist are you? Will you go to all of the cathedrals and museums? Will you take a late night bar tour? I dislike this - too gamey for me.

## 2. ET Processes and Artifacts

I like the model based on 19th century explorers. They were given charters by their governments explaining their goals, they explored, while they explored they logged and they collected, and when they returned there was a debriefing.

This may feel a bit gamey, but I think each of these steps helps get better results.

### 2.1. Charter

Draw up a goal or goals for the exploration. Also, call out things that are out of scope, so that expectations are set.

Time-box it.

A great place for this is in your task tracker.

### 2.2. Briefing

Ready to go? Check with a stakeholder or two first, often the dev area owner, sometimes a PM.

Look over the charter with them and see if there's anything else you should know before you start.

Let them know that you'll circle back afterward to debrief, too.

### 2.3. Exploration

Go. See what you can find.

If you find an obvious bug, feel free to file it and note the bug number in your log. Anything else that's interesting or questionable in any way . . . log it.

Try to reach your goal. It's ok to follow little rabbit trails for a short time, but if you're sidetracked for too long, just log it as an area for future exploration and get back on track.

#### 2.3.1. Logging

Feel free to log anywhere you like. I always put my log into the task in the tracker at the end of the exploration phase - showing my work and leaving info for anyone else interested in the area.

### 2.4. Debriefing

Circle back to the same folks you briefed with at the beginning and go over your log with them.

Chances are you found a bunch of questionable things and you can figure out now whether they're bugs or not.

Also, get feedback about the things you thought warranted future exploration. If there's agreement, feel free to file some test charters for those in the task tracker and link them to the current task.
