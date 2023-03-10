+++
title = "Modern Software Development"
outputs = ["Reveal"]
+++

## Modern Software Development

Slides: [https://bit.ly/workshop-msd](https://bit.ly/workshop-msd)

{{% note %}}
* Who am I?
* What makes me qualified to run this workshop?
* What we do at Improwised Technologies.
* Who are you? Which semester?
* Why this workshop?
  * Final year projects are same over last decade I have been working with students
  * Too much "gap" to fill between professional work and academia
  * I'd like you to focus on grander projects, and not worry about the nitty-gritty stuff
{{% /note %}}

---
## Introduction

* What makes a good software
* How to prototype fully functional software quickly
* Utilise free and OSS tools to make them do your work for you

{{% note %}}
5m
{{% /note %}}

---
### Programming Myths

* Programmers sit all day and write code
* Most important skill for a programmer is knowledge of programming language
* Programmers program, testers test
* Most theory we learn as part of curriculum is not useful

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

---
### Programming is like Writing

* Documentation -> Humans. Code -> Computers.
* What makes a good writer?
  * Knowledge of English?
  * Ability to type fast?
  * Knowledge of MS Word/Google Docs?

**No.**

{{% note %}}
20m

* All of the above are necessary, but not sufficient to be a good writer.
* Most people focus on languages, tools, and frameworks instead of patterns and processes
* Like a well-written story, well-written software is art.

What makes a good programmer then?

* Understanding and modeling the right problem: Solving a wrong problem is more detrimental than not doing anything.
* Communication - working on a team requires communicating your ideas and understanding other people's ideas
* Data Structures, Algorithms, and Design patterns - Data structures are like vocabulary. Many smart people before us have worked out efficient ways to solve certain problems. Why reinvent the wheel? "Those who do not learn history are doomed to repeat it".
* Simplicity of solution - The best code is no code at all

{{% /note %}}

---
### Prerequisites

* Node.js (http://nodejs.org/en/download)
* Visual Studio Code (https://code.visualstudio.com/download)
* Git (https://git-scm.com/downloads)
* Github CLI (https://cli.github.com/)

{{% note %}}
35m

* How many of you have built a software, however small?
  * How many of you have built it as part of a team?
  * How many with teams with more than two promgramming members?

{{% /note %}}

---
#### Revision Control

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
38m
{{% /note %}}

---
#### Workshop Template Setup

* Create a github.com account and generate [token](https://github.com/settings/tokens)
* Visit https://github.com/improwised/emi-calculator, and hit "Fork" button
* Enable Github Pages on your fork of the template.

![Github Pages](images/configure_github_pages.png)

---
#### Workshop Template Setup

* Configure local git to add your name and email

```bash
git config --global user.name "<Your Name>"
git config --global user.email "<Your Email Address>"
```

{{% note %}}
45m
{{% /note %}}

---

* Clone the codebase from your fork
* Open terminal/git bash/powershell

```bash
gh repo clone <your-username>/emi-calculator
cd emi-calculator
npm install
```

{{% note %}}
55m

* How many of you use command line? Dos or linux shell?
* How many of you are afraid of command line? Why?
{{% /note %}}

---
### Getting Familiar With The Code

(Both the workshop codebase and VS Code)

{{% note %}}
60m

* Open local copy in VS Code
* Intro to problem and code structure. Show them values.
* Show around git features of VS Code - branch, push, gutter
* Run program
* Explain and run tests

{{% /note %}}

---
#### Unit Tests

```bash
# Linux
npm run test
# Windows
npm run test-win
```
{{% fragment %}}
Does it work? Is anything missing?
{{% /fragment %}}

{{% fragment %}}
Off-by-one error in the loop

```diff
- for (let i = 0; i <= installmentsNumber; i++) {
+ for (let i = 0; i < installmentsNumber; i++) {
```

Run the tests again!
{{% /fragment %}}

{{% note %}}
65m

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

Add new test case to `tests/emi.test.js`

```js
test('Should throw an error on negative interest rate', () => {
  expect(() => EMI.Loan(10000, -1, 10)).toThrowError('wrong parameters: 10000 -1 10')
});
```
{{% /fragment %}}

{{% fragment %}}
Run tests

```bash
npm run test
npm run test-win
```

{{% /fragment %}}


{{% note %}}
75m

* Run tests, and observe failing test
{{% /note %}}

---
#### Negative test case

{{% fragment %}}

Commit

```bash
git add tests/*.test.js
git commit -m "Add test to validate whether Loan() allows negative values"
```
{{% /fragment %}}

{{% fragment %}}
Linting

```bash
npm run lint
```
{{% /fragment %}}

{{% fragment %}}
* Remove extra semicolons, and commit again

```bash
npm run lint-fix
```
{{% /fragment %}}

{{% note %}}
85m

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
// function Loan
if (!amount || amount <= 0 ||
   !installmentsNumber || installmentsNumber <= 0 ||
   !interestRate || interestRate <= 0) {
  throw new Error(`wrong parameters: ${amount} ${installmentsNumber} ${interestRate}`)
}
```
{{% fragment %}}
Commit and push

```bash
git add src/emi.js
git commit -m "Disallow negative value for all parameters"
git push origin <branch-name>
```
{{% /fragment %}}


{{% note %}}
95m

{{% /note %}}

---
#### Contributing Back

* Create a Pull Request from `<branch-name>` to `master`
* Watch CI job run and succeed

{{% note %}}
100m

* Role of merge requests
  * Code reviews
  * Running the problem by a second set of eyes
* Continuous Integration
  * Automated linting, testing and even deploying
  * Push and forget. You get an email if something goes wrong.
  * CircleCI manifest
{{% /note %}}

---
#### Continuous Deployment

* Observe the deployment at [https://\<username\>.github.io/emi-calculator/](https://improwised.github.io/emi-calculator/)
* Observe the Deployment Pipeline at [https://github.com/\<username\>/emi-calculator/actions/workflows/pages/pages-build-deployment](https://github.com/Improwised/emi-calculator/actions/workflows/pages/pages-build-deployment)

{{% note %}}
105m

{{% /note %}}

---
#### Bonus

* Dependabot Configuration (.github/dependabot.yml)
* [Probot Settings Github Application](https://probot.github.io/apps/settings/) (.github/settings.yml)

![Settings](images/settings_github_app.png)

{{% note %}}
110m

{{% /note %}}

---
#### Summary

* Implement new features in parallel in their own git branches.
* Use linting and pre-commit hooks to ensure standard and error-free code.
* Utilize Automated Tests and Continuous Integration/Deployment to record a repeatable test-build-deploy process.
* Use Dependabot and auto-merge to ensure your application is always patched against known security vulnerabilities.

{{% note %}}
112m

{{% /note %}}

---
## Open Source Software

* OSS Projects are not just Software, they are also communities
* Opportunity to learn from code written by world-class developers
* Learn how big software is built and managed.
* All of the above, for free!
* Try your hand at contributing to existing OSS Projects
  * https://firstcontributions.github.io/
  * https://github.com/MunGell/awesome-for-beginners

{{% note %}}
115m

* How many of you have used open source software before?
* Communities are amazing if you think about it. People who don't know each other work together to build and improve the same piece of code.
{{% /note %}}

---
### Open Source all your projects

* You learn from each other.
* You get to practice how to build software the way startups and large companies build it.
* You get to use state-of-the-art tooling. For free!
* It's like a resume. Your work speaks for you.

{{% note %}}
117m

{{% /note %}}

---
### Project Tips

* Address a need. Build something that you wish existed.
* Don't jump directly to writing code. Understand the problem.
* Use Github and other free tools. Some of the most useful ones are:
  * [Vercel](https://vercel.com/) & Github Pages (Build Previews and zero-config Serverless Deployments)
  * AWS/GCP/Azure/Oracle has free tier/credits for new registrations
  * Firebase (Mobile app backend)
* Use frameworks/boilerplate wherever feasible.

{{% note %}}
120m

* Choosing Problem: Content/data driven problems are common. Gather real data where possible.
* Pick something that requires more deliberation than simple CRUD operations.
* Boilerplates/Frameworks make prototyping faster.

{{% /note %}}

---
### Thanks!

**Presented By:** Monika Gorakhiya, Munir Khakhi

**Assisted By:** Tapan, Payal, Nirav, Shaktiraj, Jay, Devarshi 

Improwised Technologies Private Limited
[improwised.com](https://www.improwised.com)

Feedback: [http://bit.ly/sd-workshop](http://bit.ly/sd-workshop)
