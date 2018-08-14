# UC Davis - ServiceNow Story Share

## What is going on here?
This repository is filled with update sets that were developed at UC Davis (or links to other repositories that are sourced applications) for UC sharing use at UC CSC.

## Structure
Below you will find an explanation of each application along with descriptions of what is needed to implement it in your instance.

## Questions?
Contact Earl Duque at eduque@ucdavis.edu or find me on the UC Tech slack workspace.

## Updates/Stories/Enhancements

###### Advanced Filters

**Description:** Adds a new dynamic filter to be able to say "list contains an email address". Adds new filter queries that allows better tag filtering. Adds new filter queries that allows for email addresses.

**Difficulty to implement:** None.

**Instructions:** Import and commit update set.

###### Attach KB articles to Incidents

**Description:** Allows group managers to enable a setting that when an incident is created for their group (or transferred to their group), the email that is sent to the user triggers a mail script that will automatically query the knowledge base articles that are related to the short description of the indent and include the top three articles in the email. The user then can elect to close their ticket if an article answers their question. The group manager can also elect to have specific articles always show up in one of three slots.

**Difficulty to implement:** High. Needs knowledge of events, mail scripts, notification configuration, and portal page configuration.

**Instructions:** Import and commit update set. Edit mail script to point to the knowledge bases you need, change any URL/page links to your portal. Add the new widget to a portal page for landing. Make sure mail script points to that portal page.

###### Automated Scrum Tasks and Story Enhancements

**Description:** Adds new fields to Agile Development. Also adds "Scrum Task Automation" to the story form that allows you to dictate what scrum tasks are created automatically upon creation.

**Difficulty to implement:** Low. Requires to be on Agile 2.0

**Instructions:** Ensure you have upgraded to Agile 2.0 and then import and commit update set. If you had any rm_story form configuration changes, make sure to add those back in because this update set will overwrite the form design.

###### Automatically start a catalog item based on a previous RITM

**Description:** Installs a variable set that can included on any request catalog item that allows you to add "&sysparm_ritm=" + a sys-id of a previously submitted request item of the same catalog item. When going to the new link, it will automatically fill out the form with the previous RITM's values, which helps the submitted fill out forms quickly if they submit the same form all the time with similar values.

**Difficulty to implement:** Low. Inclusion of variable set is easy but you have to figure out how you want to provide the "resubmit" link to the user.

**Instructions:** Import and commit the update set. Add new variable set to a catalog item. Go to the catalog item submission form and add &sysparm_ritm=[sys_id] to the URL.

###### Queue Manager

**Description:** Allows group managers to turn on an option for their group that when an incident is assigned to that group, the incident will automatically be assigned to someone within that group. The Queue Manager will only assign to users that have logged in sometime that same day and the person it picks is dependent on who has gone the longest without receiving an assignment. If the group has business hours then the Queue Manager only runs during business hours, otherwise it defaults to an 8am-5pm Monday-Friday schedule. The group manager can also determine the amount of time delay that there is before the Queue Manager assigns an incident, allowing for more or less time for a ticket to be manually assigned before Queue Manager activates.

**Difficulty to implement:** Low. Some knowledge of form design is needed to ensure your previous custom form design doesn't disappear.

**Instructions:** Import and commit this update set. If you had any sys_user_group form configuration changes, make sure to add those back in because this update set will overwrite the form design.

###### SLA Definition Enhancements

**Description:** Instead of having to make a new workflow for every different SLA process, instead this update set installs a new "default SLA workflow" for SLA Definitions. When selected, a new section appears on the SLA Definition form allowing for the SLA to be set up on the definition instead of the workflow. The definition can now be set to notify of warnings and breaches at 15, 30, 50, 60, 75, 90, and 100% of the SLA duration and now can notify any combination of ticket's assignee, ticket's group (manager, members, or owner), specific users, or specific groups (manager, members, or owner).

**Difficulty to implement:** Low, knowledge of field creation is needed.

**Instructions:** The update set expects a reference field called u_owner on the sys_user_group table, you'll need to add this field in first or else you will need to modify the update set to avoid errors. Once this is done you can import and commit this update set.

###### Task Status in Service Portal

**Description:** Allows users to display a subset of records in a more appealing view in the portal. It can be configured via the following URL parameters.
* &table=[table_name] - to specify the table you wish to use (for example, &table=incident)
* &query=[encoded query] - to specific which subset of records to filter by. You can create this encoded query automatically by going to a list in ServiceNow, creating a filter on the list, and then right-click the filter and select "copy query" (for example, &query=active=true^assigned_toDYNAMIC90d1921e5f510100a9ad2572f2b477fe is the encoded query for Active is true and the Assigned to is me).
* &stater_order=[values separated by commas] - to force the display of certain columns since by default, the task status page only displays states that are currently being used by the records being displayed. (for example, &state_order=1,2,4,5,6,7 forces all incident states to display even if the subset of records aren't using all of them).
* All of the above parameters can be combined, for example: This URL will display Incident table records that are active, assigned to me (the logged in user), and also display all states despite the records displayed not using some of them.
* If no parameters are provided, the task status page defaults to active incidents assigned to the logged-in user.
* Additionally, two pre-configured task status pages have been created for internal use by IET Service Management for tracking story progress.
* The widget updates live and doesn't require refreshes.

**Difficulty to implement:** None. No pre-configuration needed.

**Instructions:** Import and commit this update set then go to /sp?id=task_status (or substitute sp for your portal name)

###### ServiceHub

**Description:** Pull a demo-friendly version of the UC Davis ServiceHub into your instance. This installs the ServiceHub as sourced application within your environment.

**Difficulty to implement:** Low to medium, deals with ServiceNow studio and github but if you follow the instructions, it should not be difficult.

**Instructions:** https://ucdavis.box.com/s/c7g3ssajtlwivxp6oiwjspnkg8s5o8tz

###### Raffle Drawing App

**Description:** Installs a sourced-application, portal friendly (in fact, it primarily uses portal for its main functionality), raffle drawing app. From the portal interface, you can create raffles, add entries individually or en masse, and draw winners (which you then can elect to redraw with or without first removing them from the entry pool).

**Difficulty to implement:** Low, although you need to know how to import github repos into a source control in ServiceNow, the instructions are provided below.

**Instructions:** Go to https://github.com/earlduque/ServiceNow-Raffle and fork it to your own github account, take note of the new URL that is created for the repository. In your instance, go to System Applications -> Studio. Upon studio launching, select "Import from source control" and input the URL from ealier along with your github username and password, and select "Import". Upon completion, you can go to /sp?id=raffle (or substitute sp for your portal name) to get started.

###### Custom autofill

**Description:** The Custom Autofill tool allows users to designate automatically populating fields and their values in the incident form. After settings have been designated in Custom Autofill, each time a new incident record is opened, the specified fields will populate with the specified values. This tool is a useful time saver for users that frequently create incidents on behalf of callers, such as help desk analysts.

**Difficulty to implement:** Low to medium? I think? I haven't tested too much on how it would interact with non Davis instances but it **should** be fine. The only thing is that for definining a guest name on ticket's that are for non-users, we have a custom field for that part, so you will either need to add that custom field or edit the code to ignore it, or leave it as is and don't use it for guests.

**Instructions:** Go to https://github.com/earlduque/sn-user-preferences and fork it to your own github account, take note of the new URL that is created for the repository. In your instance, go to System Applications -> Studio. Upon studio launching, select "Import from source control" and input the URL from ealier along with your github username and password, and select "Import". Upon completion, you can go to "Custom Autofill" in your filter navigator to get started. More usage instructions can be found here: https://ucdavisit.service-now.com/servicehub/?id=ucd_kb_article&sys_id=48357a75db245b00d1a55c98dc96195a

###### Better Order Guides in the portal

**Description:** The out-of-box order guide page and widget isn't the most friendly because it forces the user to have to scroll up just to get back to the request item picker. We adjusted the widget so that the menu follows the user's scrolling, making it a lot more easier for user's to navigate longer order guides in the portal.

**Difficulty to implement:** Low. Very basic knowledge of widgets needed.

**Instructions:** Clone the order guide widget, and then replace the code with the code found at https://github.com/earlduque/SC-Order-Guide-Fixed. Add this widget to a new page.
