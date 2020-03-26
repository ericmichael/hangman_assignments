# Homework: DevOps Setup + Pass tests

#### Story

There was a *now infamous* time at GameRiot (on a larger project) where a developer made huge mistake. Not to name names, but his name was Dave. He was a rockstar researcher from MIT who had written a ton of papers on low-level network optimization algorithms. He once pushed some network code directly to master and basically broke multiplayer for any **Duty of War** players who got the update. This was before GameRiot had their stuff together. You can imagine how *angry* Mr. Stark was (thats what everyone calls him). Literally, GameRiot's stock dropped overnight and caused Mr. Stark's shares in GameRiot to lose **millions** in value. **Duty of War** is their flagship game and they make a *killing* in in-app purchases. Hats and weird stuff. Needless to say, that developer did not last long at GameRiot. Anytime something breaks in production at GameRiot now, it's called *pulling a Dave*. No one wants to be caught *pulling a Dave*.



Rick was a little careless in his workflow. He thought as long as he wrote tests that he didn't have to use version control, yet. He figured it was a brand new project, that he could wait on that. He didn't realize that at any moment in time, new people can be brought onto a team, or you could leave a team. It is important to use version control so that you have a history of all your changes. But with the right tools and setup, you can be sure that the **master** branch of your code is always working. You can also make sure that all new code you add must be reviewed by someone else before it gets merged to **master**. This helps catch any missing tests, style issues, or other bugs. 



Your direct supervisor, Edgar Gutierrez has been tasked with making sure you continue working on this project correctly. Setup Github for correctly, protect master, configure for code review, setup CI/CD, and fix the bugs in the project. 



## DevOps

**DevOps** is a set of practices intended to reduce the time between committing a change to a system and the change being placed into normal production, while ensuring high quality**.**

DevOps (a clipped compound of "development" and "operations") is a software engineering culture and practice that aims at **unifying software development (Dev) and software operation (Ops).**

**DevOps** is the combination of cultural philosophies, practices, and tools that increases an organization’s ability to deliver applications and services at high velocity: evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes. This speed enables organizations to better serve their customers and compete more effectively in the market.



#### Some Key Concepts in Dev Ops

**Rapid Delivery**

Increase the frequency and pace of releases so you can innovate and improve your product faster. The quicker you can release new features and fix bugs, the faster you can respond to your customers’ needs and build competitive advantage. Continuous integration and continuous delivery are practices that automate the software release process, from build to deploy.

**Improved Collaboration**

Build more effective teams under a DevOps cultural model, which emphasizes values such as ownership and accountability. Developers and operations teams collaborate closely, share many responsibilities, and combine their workflows. This reduces inefficiencies and saves time (e.g. reduced handover periods between developers and operations, writing code that takes into account the environment in which it is run).



#### Continuous Integration

Continuous Integration is the process of merging code of all developers into a main source code. CI tools help find bugs faster by checking that any new changes don't break existings tests and don't cause builds to fail. If the proposed changes can be successfully integrated, then they are allowed to merge into the main source code.

The basic concept is that:

* We have a test suite that each developers runs on their own macine
* When they commit their code to a shared version control repository, the tests are run again in a clean environment, "integrated" with code from other developers.

This helps ensure there's nothing specific to the developer's machine making the tests pass.

When a build fails, we get alerts via email (and possibly Slack, or text message) and we see a backtrace that gives us a hint for how to "fix the build."

When we write the fix and commit to version control again, we'll get a "passing build" alert via email. Click the alert and we see the passing build.

Green is good.

CI test runs can be configured to be triggered based on various events. We will trigger test runs on all "pull requests" and updates to pull requests. 



#### Continuous Delivery

Continuous Deliver (CD) is an extension to continuous integration where the working software can be released to the end users at any time. The process of continuous delivery adds extra steps to the above mentioned CI process, which are:

- Packaging application;
- Code Sign (if needed);
- Deploying the application to specific environments.

With continuous delivery the software teams can achieve fully automated, low risk, and low cost releases. This process enables one click deployment where you can get the releasable build whenever needed. However, manual intervention is always required to deploy the software to production. In continuous deployment, there is no manual intervention, the committed code reaches production straightaway.



## Git Feature Branch Workflow

The core idea behind the Feature Branch Workflow is that all feature development, improvements, and bug fixes should take place in a dedicated branch rather than the `master` branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. When combined with Pull Requests, Code Review, and CI tools, this means that the `master` branch will never contain broken code.

Feature branches should have descriptive names and many organizations will have the developers prefix the name of the branch with their initials. 

Feature branches can be pushed to Github, but cannot be merge into master without going through the company's workflow pipeline.



**Feature Branching Overview**

* All improvements take place in a dedicated branch rather than the `master` branch
* Avoid including files in source control that are specific to your development machine or process.
* Delete local and remote feature branches after merging.
* Perform work in a *feature* branch.
* Use a pull request for code reviews.



# Homework

#### Step 1: Setup the workflow

**Setting up Github**

1. Accept the Github Classroom assignment

2. Follow the directions in this video


[![Alt text](https://img.youtube.com/vi/Z9Vl7o38xpQ/0.jpg)](https://www.youtube.com/watch?v=Z9Vl7o38xpQ)


**Setting up CodeMagic**

1. Setup Continuous Integration

[![Alt text](https://img.youtube.com/vi/2in1naZ1Kpo/0.jpg)](https://www.youtube.com/watch?v=2in1naZ1Kpo)

2. Setup Continuous Delivery

[![Alt text](https://img.youtube.com/vi/u3x1GN0WJ7w/0.jpg)](https://www.youtube.com/watch?v=u3x1GN0WJ7w)

#### Step 2: Restore Working Version / Git Flow Practice

**Your Job:**

Video Walkthrough: 

[![Alt text](https://img.youtube.com/vi/tfnxW7bNL7k/0.jpg)](https://www.youtube.com/watch?v=tfnxW7bNL7k)

Written steps:

1. Create a branch but **prefix your branch name with your initials**. For me, Eric Martinez I would use:

    ```
    git checkout -b em-restore-working-version
    ```

2. Add just enough code to pass the tests (don't modify the tests).

3. Push your changes to Github.

   ```
   git push origin em-restore-working-version
   ```

4. Submit a pull request. 

5. CodeMagic will tell you if you failed any tests. If you pass all the tests, ask Edgar Gutierrez in Discord for a Code Review.

6. Once accepted, checkout the master branch.

   ```
   git checkout master
   ```

7. Delete your remote feature branch.

   ```
   git push origin --delete em-restore-working-version
   ```

8. Delete your local feature branch.

   ```
   git branch --delete em-restore-working-version
   ```

9. Pull the latest changes into your local master branch.

   ```
   git pull
   ```
