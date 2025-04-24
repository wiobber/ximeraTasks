# This repo is for development of Ximera-Modulus instrumentation

The file firstActivity.tex contains some very simple multiple-choice questions.  
The file secondActivity.tex contains more questions.

## How to test/deploy from VSCode:

* Generate a GPG key (use the 'Extra' button in the lower left corner, and select the last option)
* (only when NOT in a Codespace) Start a local ximeraServer (also from the Extra menu; now first option)
* Push the 'SERVE' button
* (on your PC) go to localhost:2000
* (in a Codespace) start a browser from the 'PORTS' tab for forwarded 'localhost:2000' (a globe icon appears on hovering over the first line)
* Optionally, manually edit the file firstActivity.html
* Run (in a bash shell):
   * ./xmScripts/xmlatex frost
   * ./xmScripts/xmlatex serve
* An orange 'Update' button should appear on the firstActivity webpage, that will show the changed firstActivity.html -- push this button.

## Page point breakdown

All answerables (\answer, multipleChoice, selectAll, wordChoice) must be coded inside a LaTeX environment, e.g. problem, exercise, theorem, example — any environment — basically a "box."

If a page has no answerables, students get completion credit for landing on the page. I suppose if I could "ask for the Moon," I'd like for **students to have to scroll to somewhere near the bottom of the content.** 

If the page has environments, some with answerables, then  
**the total page score is determined by the number of environments with answerables.**  
Technically, the total page score is 1, with each environment containing an answerable being worth 1/(number of environments with answerables). If environments are nested (boxes within boxes), any answerable within the nests triggers this to be counted.

When nested environments have multiple answerables — say, *n* answerables, even within different levels of nesting — we want the total score of the problem to be determined by the total number of answerables. So each answerable within this environment would be worth  
1/((number of environments with answerables)) × (1/(number of answerables within this environment)).

(Note — this is somewhat different than how it currently works, but I think this is better and more clear to all users: authors, instructors, students.)

### Example

Suppose a page has 10 outermost theorem-like environments (boxes). If 6 of these theorem-like environments have answerables, then this page is worth 1 point, with each of the outermost boxes worth 1/6 points.

Now suppose that 1 of these 6 actually has 5 answerables in it. Then each of those is worth  
1/(6 × 5) points.

Now suppose that we have a nested series of environments — say, 3 levels of nesting — one with 7 answerables, one with 8 answerables, and one with 9 answerables. Each of these answerables is worth  
1/(6 × (7 + 8 + 9)).
