+++
title = "My presentation"
outputs = ["Reveal"]
+++

# Modern Software Development Workflows

{{% note %}}
* Who am I?
* Who are you? Which semester?
* Why this workshop?
  * Final year projects are same over last decade I have been working with students
  * Too much "gap" to fill between profrssional work and academia
  * I'd like you to focus on grander projects, and not worry about the nitty-gritty stuff
{{% /note %}}

---
## Introduction

* How to prototype fully functional software fast
* Utilise tools and automation to make them do your work for you

{{% fragment %}}#### But first, let's bust some myths {{% /fragment %}}

{{% note %}}
5m
{{% /note %}}

---
{{< markdown >}}
#### Misconceptions About a Programmer's Job

<!-- .slide: style="color:red" -->
* {{% fragment %}}Programmers sit all day and write code{{% /fragment %}}
* {{% fragment %}}Most important skill for a programmer is knowledge of programming language{{% /fragment %}}
* {{% fragment %}}Testing is not a programmer's job, it's a tester's job{{% /fragment %}}
* {{% fragment %}}What you learn in college is mostly obsolete{{% /fragment %}}

{{% note %}}
15m

* Collaborating with stakeholders and colleagues is where large chunk of the time is spent
* Programmers spend more time reading existing code and thinking than writing/changing new code.

* Most important skills for a programmer are communication skills closely followed by logic and reasoning.
* Programming is communicating in a way - writing precise instructions for computers that take every instruction of yours literally.
* Learning new programming language is relatively easy once you know one of them. Learn new languages. Will expand your horizons.

* Testing is important part of the programming feedback loop. Only way to make sure what you wrote works as intended.
* Software testers are responsible for finding gaps in implementation details rather than making sure your piece of code works.

* Most important things you learn in college are fundamentals. Data structures, algorithms, operating systems, networks, compilers, design patterns etc.
* The "gap" is because of continuous change in programming paradigms. For instance, nowadays programmers are more of assemblers of code than writers of them.
* Depend on third-party modules, and open source software to boost productivity

{{% /note %}}

{{< /markdown >}}

---
#### Version Control Systems

* Collaboration
* Accurate version tracking, and restoring to previous versions
* Code Archeology - Auditable history of who did what, and why.
* Backup - more than one copy of code and its history

---
### Git

* Distributed - all history and files travel with checkouts
* Immutable - Nothing can alter historical commits, increasing auditability.
* Fast
* Widely used, popular
* Flexible workflows

{{% note %}}
20m
{{% /note %}}


---
### Prerequisites

* Node.js (http://nodejs.org/en/download)
* Visual Studio Code (https://code.visualstudio.com/download)
* Git (https://git-scm.com/downloads)
* All-in-one bundle (TODO: Link)
![git](images/git.png)

{{% note %}}
35m

* How many of you have built a software, however small?
  * How many of you have built it as part of a team?
  * How many with teams with more than two promgramming members?

{{% /note %}}

---
#### Workshop Template

* Create a gitlab.com account
* Visit https://gitlab.com/improwised/sd-workshop, and hit "Fork" button
![fork](images/fork.png)

{{% note %}}
40m
{{% /note %}}

---

* Clone the codebase from your fork
* Open git bash

```bash
git clone https://gitlab.com/<your-username>/sd-workshop.git
cd sd-workshop
npm install
```

{{% note %}}
45m

* How many of you use command line? Dos or linux shell?
* How many of you are afraid of command line? Why?
{{% /note %}}

---
### Getting Familiar With The Code

(Both the workshop codebase and VS Code)

{{% note %}}
50m

* Open local copy in VS Code
* Intro to problem and code structure. Show them values.
* Show around git features of VS Code - branch, push, gutter
* Run program
* Explain and run tests

{{% /note %}}

---
#### Unit Tests

{{% fragment %}} Does it work? Is anything missing? {{% /fragment %}}

{{% note %}}
55m

* Why automated tests?
  * Repititive, so more likely to have lapses without it
  * Quicker than manual ones
  * Provides sense of security that the code works
* Explain structure and run tests
  * Jest
  * Coverage report

{{% /note %}}

---
#### Negative test case

```
git checkout -b <branch-name>
```

{{% fragment %}}

Add new test case to `tests/bill-split.test.js`

```js
test('Negative currency should not be allowed', () => {
    expect(() => {
        BillSplitter.split(-100, 2)
    }).toThrow()
})
```
{{% /fragment %}}

{{% fragment %}}
Run tests

```bash
npm test
```

{{% /fragment %}}


{{% note %}}
60m

* Run tests, and observe failing test
{{% /note %}}

---
#### Negative test case

{{% fragment %}}
Commit

```bash
git add tests/*.test.js
git commit -m "Added negative test case for bill-split"
```
{{% /fragment %}}

{{% fragment %}}
Linting

```bash
npm run lint
```
{{% /fragment %}}

{{% fragment %}}
* Add missing semicolons, and commit again

```bash
./node_modules/.bin/eslint --fix .
```
{{% /fragment %}}

{{% note %}}
65m

* Run tests, and observe failing test
* Attempt to commit code
* Linting
  * Avoids errors
  * Enforces code style - important that whole codebase has a consistent style for readability
* Git hooks

{{% /note %}}

---
#### Fix code

```js
module.exports = {
    split: function (totalBill, people) {
        if (totalBill >= 0) {
            return Math.ceil(totalBill / people);
        } else {
            throw new Error('Bill value cannot be negative');
        }
    },
};
```
{{% fragment %}}
Commit and push

```bash
git add src/bill-split.js
git commit -m "Disallow negative bill value"
git push origin <branch-name>
```
{{% /fragment %}}


{{% note %}}
70m

{{% /note %}}

---
#### Contributing Back

* Create a Merge Request from `<branch-name>` to `master`
* Watch CI job run and succeed

{{% note %}}
85m

* Role of merge requests
  * Code reviews
  * Running the problem by a second set of eyes
* Continuous Integration
  * Automated linting, testing and even deploying
  * Push and forget. You get an email if something goes wrong.
  * Gitlab CI manifest
{{% /note %}}

---
### Thanks!

Rakshit Menpara

[improwised.com](https://www.improwised.com)

Feedback: [http://bit.ly/sd-workshop](http://bit.ly/sd-workshop)
