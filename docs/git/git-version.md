# Git Versioning

The goal of adding a new dependency to your code is to avoid reinventing the wheel. If there is code already available that does what you want, normally you would prefer to re-use it (there are exceptions, though) rather than investing your time in re-writing new code to solve the same task. On the other hand, once your software project has matured over time and is ready for production it may end up being a dependency for other software projects as well.

Initially, re-using software packages as much as possible looks like the best way forward to save time and effort in the long run; and it is indeed true. However, creating dependencies with other software packages also brings its own disadvantages, specially when the number of dependencies becomes larger and larger. Grouping off-the-shelf functions into software packages and defining dependencies between them has been traditionally at the core of software development.

If you're building libraries, products or any other software system, versioning is usually a pretty big deal. It's the only way to determine what version of that library, product or system you're looking at. Before an organization settles on a versioning strategy, many discussions have been held on what constitutes a major release versus a minor release, how to version the component from a marketing perspective, and how to deal with bug fixes. In addition to that, if that software system involves a library or framework, or just component, then you'd be pretty interested to know when an update to that component involves breaking changes.

From the version of an app you should, for instance, be able to guess whether it’s a bugfix or it has introduced new features. Without properly set version codes you could totally lose your compass on what’s happening. So, when you set the version of your software always be careful and remember that, given a major.minor.patch version number, you should increment:

* patch when you make bug fixes
* minor when you introduce new features
* major when you make changes that break backwards-compatibility or completely change the user experience

That being said, in the daily practice, if you want to start with a development phase before going to production the simplest thing could be to start with a 0.1.0 version number and increment minors at each new development release. Also keep in mind that if you’re working on a production project it’s always a good idea to start with a 1.0.0 version code.

## GitVersion Docs

GitVersion is a tool to help you achieve Semantic Versioning on your project. Semantic Versioning is all about releases, not builds. This means that the version only increases after you release, this directly conflicts with the concept of published CI builds. When you release the next version of your library/app/website/whatever you should only increment major/minor or patch then reset all lower parts to 0, for instance given 1.0.0, the next release should be either 2.0.0, 1.1.0 or 1.0.1. Bumping one of the version components by more than 1 in a single release means you will have gaps in your version number, which defeats the purpose of SemVer.

![Major, minor, and patch version numbers](./assests/git-versioning.png)

Fortunately, the open-source community has solved both of these problems for us. First, we have semantic versioning, which unambiguously defines how to update your version when you do hot fixes and patches, minor back-wards compatible improvements or breaking changes. They even define how you should post-fix your version numbers to denote pre-releases and build numbers. Assuming all decent software project are using Git these days, then the other problem is solved by following the Git branching workflows we've discussed earlier.

Wouldn't it be cool if some kind of tool existed that used the names of the branches and the tags on master (representing the production releases) to generate the proper version numbers for you? Well, once again, the open-source community comes to the rescue. Jake Ginnivan and the guys from ParticularLabs, the company behind NServiceBus, have build just that and named it GitVersion. So let's see how that works. GitVersion describes in detail on what branch you do your main development work, how you stabilize an upcoming release and how you track production releases.

GitVersion is able to calculate the version based on the state of your git repository. This requires some getting used to, but GitVersion is like a pure function that calculates the semantic version of any given commit based on three things:

* the nearest tag
* the commit messages between this commit and the nearest tag
* the name of the branch

It can be configured with a YAML file and it supports branching models like GitFlow and GitHubFlow (also called Feature branch workflow). Lets see how GitVersion calculates the semantic version.

Watch this interesting video <https://youtu.be/sVzIZSo8jPI>
