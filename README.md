# This repo is for development of Ximera-Modulus instrumentation

The file firstActivity.tex contains some very simple multiple-choice questions.
The file secondActivity.tex contains more questions


## How to test/deploy from VSCode:

* Generate a GPG key (use the 'Extra' button in lower left corner, and  select the last option)
* (only when NOT in a Codespace) Start a local ximeraServer (also from the Extra menu; now first option)
* push the 'SERVE' button
* (on our PC) go to localhost:2000
* (in a codespace) sart a browser from the 'PORTS' tab for forwarded 'localhost:2000' a globe-icon appears on hoovering over trhe first line)
* optionally, manually edit the file firstActivity.html
* run (in a bash shell)
   * ./xmScripts/xmlatex frost
   * ./xmScripts/xmlatex serve
* an orange 'Update' button should appear on the firstActivity-webpage, that will show the changed firstActivity.html


## Basic point breakdown.

All answerables (\answer, multipleChoice, selectAll, wordChoice) must be coded inside a LaTeX environment, e.g. problem, exercise, theorem, example, any environment - bascially a "box."

The page then has a lot of environments, some have answerables, some don't. 

**The total page score is determined by the number of environments with answerables**
(Technically, the total page score is 1, with each enviroment contining an answerable being worth 1/(number of environments with answerables). If environments are nested, (boxes within boxes) Any answerable within the nests trggers this to be counted. 


When nested environments have multiple answerables, say n answerables, even within different levels of nesting, we want the total score of the problem to be determined by the total number of answerables. So each answerable within this environment would be worth 1/((number of environments with answerables))*(1/(number of answerables within this environment))

(Note -- this is somewhat different than how it currently works, but I think this is better and more clear to all users; authors, instructors, students.)

### Example

Suppose a page has 10 outer most theorem-like environments (boxes). If 6 of these theorem-like environments have answerables, then this page is worth 1 point, with each of the outermost boxes worth 1/6 points. 

Now suppose that 1 of these 6, actually has 5 answerables in it. Then each of those is worth
1/(6*5) points. 

Now suppose that we have a nested series of environments, say 3 levels of nesting, one with 7 answerables and 1 with 8 answerables and one with 9 answerables. Each of these answerables is worth
1/(6*(7+8+9))




 
