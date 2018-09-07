---
layout: post
title:      "Rails App with a jQuery Front End Project"
date:       2018-08-06 19:22:48 -0400
permalink:  rails_app_with_a_jquery_front_end_project
---


The goal of [this project](https://github.com/terryblue99/my-watch-collection-v-001) is to expand upon my [previous Rails Project](https://github.com/terryblue99/my-watch-collection-v-000) by adding dynamic features, using jQuery and a JSON API to append data to existing pages without a page refresh.

**REQUIREMENTS**
1. Use jQuery for implementing new requirements 
2. Include a show resource rendered using jQuery and an Active Model Serialization JSON backend
3. Include an index resource rendered using jQuery and an Active Model Serialization JSON backend
4. Include at least one has_many relationship in information rendered via JSON and appended to the DOM
5. Use your Rails API and a form to create a resource and render the response without a page refresh
6. Translate JSON responses into js model objects
7. At least one of the js model objects must have at least one method added by your code to the prototype

As with my previous project I decided to use branches to code and test each part of my application before merging it with the master branch.

I also did the normal walkthrough of my application at the end but this time I decided to document each stage as I did so and this was very beneficial. It not only slowed down the process but by doing so it also made me more focused and diligent with that task. I even found a part of my previous project that I'd forgotten to test with the new changes.

Below is the documentation of my walkthrough:

**WALKTHROUGH**

1.	Clone the repository from Github and run the following commands in the terminal:  

      - **bundle install**  => (*installs the app gems*)
      - **rake db:migrate** => (*runs migrations*) 
      - **rake db:seed** => (*Loads the complications table with watch complications*)
      - **rails s**  => (*starts the server,  displaying the local host url*)

2.	Copy and paste the url into the browser to display the **Log in** page

3.	**Log in** or click **Sign up** to go to the **Sign up** page => [Devise](https://github.com/plataformatec/devise)/[OmniAuth](https://code.tutsplus.com/articles/how-to-use-omniauth-to-authenticate-your-users--net-22094) handles users/authorizations

4.	The home page will be displayed by the *watches#index* root route => config/routes.rb => views/watches/index.html.erb

**Options**

**Home Page**	

   Contains a list of links and a list of watches
	 
   If more than 16 watches are already saved, only the first 16 will be displayed and pagination links will appear at the 
   bottom ([will_paginate](https://github.com/mislav/will_paginate)) 
	 
   There will also be an option to change the number of watches displayed on each page 

•	If pagination links exist on the page:

1. Click **Next** or **Previous** or a number to advance to the next or previous page or the page number selected
     **- (No page refresh) - Requirement 1**
2. The click is hijacked by the assets/javascripts/watches.js event handler for **“.pagination a”** which calls the *pagination* function
3. This clears the current list of watches, gets the next page of watches, appends them to the current page, and then resets the pagination links
4. Enter or select a number in the **Watches on a page** box and click **submit** to change the number of watches displayed per page

•	Click on **Show all of my watches** link to redisplay the initial home page

•	Click on **Who makes most of my watches?** link to display the related list (*pagination process same as for all 
   watches*)

•	Click on **Show my 10 newest watches** link to display the related list

•	Click on **Add a new watch** link to add a watch => views/watches/new.html.erb => views/watches/_form.html.erb
1.   Add details for a new watch
2.  Click **Choose File** to add an image for the watch (if none chosen, default image displayed)

•	**Find a Watch**

1. Enter a watch name or part of a name in the **Search for** field and click **Search**
2. The watch/es and related maker/s will display, or if not found, the message "There are currently no watches to display! "

•	**Find a Maker**

1. Enter a full watch maker name in the **Search for** field and click **Search**
2. The maker and related list of watches will display, or if not found, the message "There are currently no watches to display! "

•	Click on a watch name link to view the watch => views/watches/show.html.erb 
   (Only the watch name is displayed initially)

**Watch Page**

   Contains a list of links and the watch details (only the watch name is displayed initially)

•	Click on **Show watch details** link to view full details of the watch (*minus complications*) 
   **- (No page refresh) - Requirement 2**
1. The click is hijacked by assets/javascripts/watches.js event handler for “**a.show_watch**”
2.  It gets the *#watch-template* handlebars template from views/watches/show.html.erb and compiles it
3.  Then calls the *showWatch* function to get the watch details and append them to  the current page

•	Click on **Show complications** link to view complications
   **- (No page refresh) - Requirement 3**
1. The click is hijacked by assets/javascripts/complications.js event handler for “**a.complications_link**” (**#load_complications**)
2. It gets the *#complications* handlebars template from views/watches/show.html.erb and compiles it
3. Then calls the *loadComplications* function to get the complications
4. If there are complications, they are sorted on name and then appended to the current page, else a message is displayed saying **There are no complications to display!**

•	Click on **Add complications** link to add complications
1. The click is hijacked by assets/javascripts/complications.js event handler for “**a.complications_link**” (**#complications_form**) 
2. It gets the *#complications* handlebars template from views/watches/show.html.erb and compiles it
3. Then calls the *loadComplications* function to get the complications
4. If there are complications, they are sorted on name and then appended to the current page, else a message is displayed saying **There are no complications to display!**
5. It then displays a form to add complications to the watch, either from the list, as a new one, or a  combination of both 
6. Select complication/s from the existing list and/or enter a new one and click **Update Watch**
     **- (No page refresh) - Requirements 4 & 5**
7. The click is hijacked by assets/javascripts/complications.js event handler for “**form#new_complication**
8. It retrieves the **action** and **params** from the form and calls the *newComplication* function
9. This uses the *Complication* prototype and the *renderComplication* function attached to that prototype to format and append the complication/s to the current page
10. Then makes an entry in the complications_watches join table (*any new complications are also added to the complications table*)

•	Click on a complication name link to display its description  => controllers/complications_controller.rb => description route => views/complications/description.html.erb
1. Click on **Back** to return to the previous page
2. **OR** Click on **Delete this complication from the watch** to delete the complication from the watch
*  An alert will display asking **Are you sure you want to delete this complication from the watch?**
*  Click **OK** to delete the complication or **Cancel** to abort
*  Only deletes the entry in the complications_watches join table and not the complications table
3. **OR** Click on **Delete this complication from the list** to delete the complication from the list
*  An alert will display asking **Are you sure you want to delete this complication from the list?**
**ALL watches will lose this complication!!!**
*  Click **OK** to delete the complication or **Cancel** to abort
*  Deletes the entry in the complications table and **ALL** related entries in the complications_watches join table
*  Returns to the previous page and displays that the complication has been deleted
*  Click on **Show complications** to refresh the complications displayed

•	Click on **Edit this watch** to edit the watch details => views/watches/edit.html.erb => views/watches/_form.html.erb
1. Click **Choose File** if adding or changing an image for the watch

•	Click on **Delete this watch** link to delete the watch => controllers/watches_controller.rb => destroy route
1. An alert will display asking **Are you sure you want to delete this watch?**
2. Click **OK** to delete the watch or **Cancel** to abort
3. Deleting the watch will also delete any related join records in the complications_watches join table
4. Returns to the initial home page

•	Click on **Show all of my watches** link to redisplay the initial home page

 **Navbar Links**

•	**My Watch Collection**
   Redisplays the initial home page

•	The signed in ID (*not a link*)

•	**Sign Out**
   Exits the application
	 
•	**Edit Profile**
   Edit email address / password

•	**Watch Education**
   Links to a website with information on “Everything You need To Know About Watches”

•	**Watches Online**
   Links to a website that sells watches

* **Twitter**
* **Facebook**
* **Google Plus**

[Here is my video walkthrough](https://youtu.be/VoPAuMnq-aU)
