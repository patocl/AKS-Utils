# Git branch antippatterns

## It let's us do more!

* Team is sprinting with multiple Stories in current sprint
* Too much work in progress
* Teeam creates one feature branch per story
* Merging code on last day of sprint
* Merge don't go well leading to issues
* Code reviews flag issue, merge rejected
* End of sprint: Nothing delived!

## Communication and trust issues!

* Developers in a team don't trust each other..
* "Jhon's code is awful and breaks all the time... So I'll work in my separate branch..."
* Result: Kicking the can and deferring the problem to later...

## Shifting priorities!

* 100's of branches
  * Lots of partially completed features scattered across branches
  * Unclear what needs to ship
* Mostly a result of unclear goals and shifting priorities...
* Management keeps shifting the goal post...
* Unable to release finished features..

## Some useful tips to improve the Git usage

* **Commit early and often** perfect later, publish once philosopy
* **Github Flow** can be used to govern overall
* **Deliver frequently** be prepared to send every single commit
* **Scrum tasks** are mapped to commits, not stories
* **Deleting branches after merge** will make your commit grpah readable
* **Continuous integration** validates master branch continuously
* **Pull requests** can be used to review code and to validate before merging back to master
* **Feature flags** should be used whenever possible
