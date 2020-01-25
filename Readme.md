# Software Development Workflows

Presentation companion to the SD Workflows Workshop.

## Instructions

This slideshow is built using [Hugo](https://gohugo.io/) and Reveal.js. Download/install hugo, and run `hugo server` from the root of this repository to build and serve the slides over a web server on [http://localhost:1313](http://localhost:1313).

```
git submodule update --init
hugo server

# Deployment to Now
now -n sd-workflows --prod public
```

## License

MIT



## Outline

* Who am I?
* Purpose: Focus on ambitious projects, and leave nitty-gritty to automation and tools
* Open Source.
  * How many of you have used open source software before?
  * How many of you have created or contributed to an open source application?
  * How many of you are thinking of making their project open source? Why not?
  * Advantages of Open Sourcing final year projects
    * It's a resume. Your work speaks for you.
    * Collaborating with your partners and others is easy
    * You get to use state-of-the-art tooling for free
* Programming is like writing
  * Programming is writing detailed instructions for a computer to follow.
  * Most people focus on languages, tools, and frameworks instead of patterns and processes
  * Knowing English, how to type, and how to use MS Word is necessary to be a good writer, not sufficient.
  * What else is important?
    * Understanding of the problem at hand - Know what you are solving.
    * Communication - working on a team requires communicating your ideas and understanding other people's ideas
    * Design patterns - Many smart people before us have worked out efficient ways to solve certain problems. Why reinvent the wheel? "Those who do not learn history are doomed to repeat it".
    * Simplicity, Separation of Concern, Performance, Security
* What does this workshop cover?
  * Process over Tools
  * Version Control, Git, and Github
  * Quick Prototyping through Boilerplate/Framework
  * Unit tests
  * Static Code Analysis/Linting
  * Automated builds and Continuous Integration
  * Pull Requests and Code Reviews
  * Continuous Deployment through Zeit Now
* Prerequisites
  * Git CLI
  * VS Code
  * Node.js
* Git
  * How it works
  * Branches
  * Clone, Pull, Commit, Push
  * Remotes
  * Github
    * Fork, Pull Requests
* Try your hand at contributing to existing Open Source Project
  * https://firstcontributions.github.io/
  * https://github.com/MunGell/awesome-for-beginners



## TODO

* Add careers page at last
* Publish Presentation to Now
* Link presentation inside itself so that others can follow
* An exercise repo in github where people contribute their name and it shows up in a list on a continuously deployed website
* Add prerequisites to a USB drive


## Extra

```
### Principles of a good Web Application

#### 12 Factors ([https://12factor.net/](https://12factor.net/))

* Revision Control
* Explicit Dependencies
* Configuration in Environment
* Backing services are external
* Separate Build, Release, and Run stages
* Make application process stateless
* Export service endpoints via port binding
* Scale out by multiplying stateless processes
* Fast startup, and graceful shutdown
* All deployment environments should be as similar as possible
* Export logs to stdout/stderr
* Run admin tasks as one-off processes

{{% note %}}
55m

{{% /note %}}

---
```
