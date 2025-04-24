
The file firstActivity.tex contains some very simple multiple-choice questions.


How to test/deploy from VSCode:

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



 