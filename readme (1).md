# About These Notes

![](https://res.cloudinary.com/briezh/image/upload/v1539805526/spaceneedle_ga_sea_ykjk40.jpg)

Welcome to GA Atlanta! This is the notes repository for our Software Engineering Immersive \(formerly known as Web Development Immersive\). You can view the content in a more searchable/friendly format on [Gitbook](https://romebell.gitbook.io/sei-1019/)!

![GA Logo](.gitbook/assets/ga_cog.png)

## Setting up the Notes locally

This is totally optional. If you choose to do this, please update every 3-6 months to get any additions/updates changes we make to the local Atlanta curriculum!

* Fork this repository
* Clone your fork to your development machine
* Setup a remote for your fork
* On your terminal, run 
```text
git remote add upstream git@github.com:romebell/SEI1019.git
```
* Install the Gitbook CLI tool by running 
```text
npm install -g gitbook-cli
```
* Preview the Gitbook by running `gitbook serve`

#### Updating your local repo

* On your terminal, run:
- Get the changes from us
```text
git fetch upstream master
```
- Add those changes to your local machine's clone
```text
git merge upstream/master
```
- Updates your `fork` on Github
```text
git push origin master
```

## Contributing to the Notes

* All contributions can be done via pull requests
* Recommended process:
  * Make changes in your forked repository \(use a separate branch\)
  * Create a pull request and be sure to be very explicit about the changes you've made
  * Ask someone on the SEI team to look at your pull request

## Schedule

Notes below are organized by topic, but they are unordered. This is because we may at any point swap new material in or switch the order of the units.

Something to know is that some of the lessons here are more historical and haven't been used in at least a couple years. For example, the Ruby lessons and the lessons in unit 1 that delve deeper into the guts of ES5 syntax like prototypal inheritance. We've elected to skip that in favor of teaching OOP during the Python unit.

### Origin of this Gitbook

Due to the changing nature of course delivery format in response to COVID-19, this course is only offered remotely at this time, and the student pool spans multiple campuses. This version of the notes is tailored for the SEI 1019, offered remotely through the Atlanta campus. It will be a working set of documents as SEI instructors continually adapt this originally campus-driven curriculum for the new demands of work-from-home life. The idea is to front-load each day with lessons in the morning, leaving the majority of the afternoon for flexibe workshop/lab time to accomodate screen-lecture attention spans and the unique demands that families and individuals face during a global pandemic and social unrest over racial injustice.

## Licensing

1. All content is licensed under a CC-BY-NC-SA 4.0 license.
2. All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.

