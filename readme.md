# UC Davis - ServiceNow Story Share

## What is going on here?
This repository is filled with update sets that were developed at UC Davis (or links to other repositories that are sourced applications) for UC sharing use at UC CSC.

## Structure
Below you will find an explanation of each application along with descriptions of what is needed to implement it in your instance.

## Questions?
Contact Earl Duque at eduque@ucdavis.edu or find me on the UC Tech slack workspace.

###### Advanced Filters
Description: Adds a new dynamic filter to be able to say "list contains an email address". Adds new filter queries that allows better tag filtering. Adds new filter queries that allows for email addresses.
Difficulty to implement: None.
Instructions: Import and commit update set.

###### Attach KB articles to Incidents
Description: Allows group managers to enable a setting that when an incident is created for their group (or transferred to their group), the email that is sent to the user triggers a mail script that will automatically query the knowledge base articles that are related to the short description of the indent and include the top three articles in the email. The user then can elect to close their ticket if an article answers their question. The group manager can also elect to have specific articles always show up in one of three slots.
Difficulty to implement: High. Needs knowledge of events, mail scripts, notification configuration, and portal page configuration.
Instructions: Import and commit update set. Edit mail script to point to the knowledge bases you need, change any URL/page links to your portal. Add the new widget to a portal page for landing. Make sure mail script points to that portal page.

###### Automated Scrum Tasks and Story Enhancements
Description: Adds new fields to Agile Development. Also adds "Scrum Task Automation" to the story form that allows you to dictate what scrum tasks are created automatically upon creation.
Difficulty to implement: Low. Requires to be on Agile 2.0
Instructions: Ensure you have upgraded to Agile 2.0 and then import and commit update set. If you had any rm_story form configuration changes, make sure to add those back in because this update set will overwrite the form design.

###### Automatically start a catalog item based on a previous RITM
Description: Installs a variable set that can included on any request catalog item that allows you to add "&sysparm_ritm=" + a sys-id of a previously submitted request item of the same catalog item. When going to the new link, it will automatically fill out the form with the previous RITM's values, which helps the submitted fill out forms quickly if they submit the same form all the time with similar values.
Difficulty to implement: Low. Inclusion of variable set is easy but you have to figure out how you want to provide the "resubmit" link to the user.
Instructions: Import and commit the update set. Add new variable set to a catalog item. Go to the catalog item submission form and add &sysparm_ritm=[sys_id] to the URL.

###### Queue Manager
Description: Allows group managers
Difficulty to implement: 
Instructions: 

###### SLA Definition Enhancements
Description: 
Difficulty to implement: 
Instructions: 

###### Task Status in Service Portal
Description: 
Difficulty to implement: 
Instructions: 

###### ServiceHub
Description: 
Difficulty to implement: 
Instructions: 

###### Raffle Drawing App
Description: 
Difficulty to implement: 
Instructions: 

###### Custom autofill
Description: 
Difficulty to implement: 
Instructions: 

###### Better Order Guides in the portal
Description: 
Difficulty to implement: 
Instructions: 
