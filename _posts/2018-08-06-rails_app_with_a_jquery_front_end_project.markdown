---
layout: post
title:      "Rails App with a jQuery Front End Project"
date:       2018-08-06 19:22:48 -0400
permalink:  rails_app_with_a_jquery_front_end_project
---


The goal of [this project](https://github.com/terryblue99/my-watch-collection-v-001) is to expand upon my [previous Rails Project](https://github.com/terryblue99/my-watch-collection-v-000) by adding dynamic features, using jQuery and a JSON API, without using remote: true.

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

      - **bundle install**  => (installs the app gems)
      - **rake db:migrate** => (runs migrations) 
      - **rake db:seed** => (Loads the complications table with watch complications)  
																		               (There are a few sample users which are commented out)  
      - **rails s**  => (starts the server,  displaying the local host url)

2.	Copy and paste the url into the browser to display the Log in page

3.	**Log in** or click **Sign up** to go to the **Sign up** page => [Devise](https://github.com/plataformatec/devise)/[OmniAuth](https://code.tutsplus.com/articles/how-to-use-omniauth-to-authenticate-your-users--net-22094) handles users/authorizations

4.	The home page will be displayed by the watches#index root route => config/routes.rb => views/watches/index.html.erb

**Options**

**Home Page**	

   Contains a list of links and a list of watches
	 
   If more than 16 watches are already saved, only the first 16 will be displayed and pagination links will appear at the 
   bottom ([will_paginate](https://github.com/mislav/will_paginate)) 
	 
   There will also be an option to change the number of watches displayed on each page 

•	If pagination links exist on the page:

1. Click **Next** or **Previous** or a number to advance to the next or previous page or the page number selected
2. The click is hijacked by the assets/javascripts/watches.js event handler for **“.pagination a”** which calls the pagination function
3. This clears the current list of watches, gets the next page of watches, appends them to the current page, and then resets the pagination links
4. Enter or select a number in the **Watches on a page** box and click **submit** to change the number of watches displayed per page

•	Click on **Show all of my watches** link to redisplay the initial home page

•	Click on **Show the maker of most of my watches** link to display the related list (pagination process same as for all 
   watches)

•	Click on **Show my 10 newest watches** link to display the related list

•	Click on **Add a new watch** link to add a watch => views/watches/new.html.erb => views/watches/_form.html.erb

•	Click on a watch name link to view the watch => views/watches/show.html.erb 

**Watch Page**

   Contains a list of links and the watch details (only the watch name is displayed initially)

•	Click on **Show Watch Details** link to view full details of the watch (minus complications)
1. The click is hijacked by assets/javascripts/watches.js event handler for “**a.show_watch**”
2.  It gets the #watch-template handlebars template from views/watches/show.html.erb and compiles it
3.  Then calls the showWatch function to get the watch details and append them to  the current page

•	Click on **Complications** link to view complications	
1. The click is hijacked by assets/javascripts/complications.js event handler for “**a.load_complications**”
2. It gets the #complications handlebars template from views/watches/show.html.erb and compiles it
3. Then calls the loadComplications function to get the complications
4. If there are complications, they are sorted on name and then appended to the current page, else a message is displayed saying **There are no complications to display!**
5. In either case a form is displayed to add complications to the watch, either from an existing list or as a new one
6. Select complication/s from the existing list or enter a new one and click **Update Watch**
7. The click is hijacked by assets/javascripts/complications.js event handler for “**form#new_complication**
8. It retrieves the **action** and **params** from the form and calls the newComplication function
9. This uses the Complication prototype and the renderComplication function attached to that prototype to format the complication/s and append to the current page
10. Then makes an entry in the complications_watches join table (new complications are also added to complications 
	        table)

•	Click on a complication name link to display its description 
1. controllers/complications_controller.rb => description route => views/complications/description.html.erb
2. Click on **Back** to return to the previous page
3. **OR** Click on **Delete this complication** to delete the complication 
*  An alert will display asking **Are you sure you want to delete this complication?**
*  Click **OK** to delete the complication or **Cancel** to abort
*  Only deletes the entry in the complications_watches join table

•	Click on **Edit this Watch** to edit the watch details => views/watches/edit.html.erb => views/watches/_form.html.erb

•	Click on **Add a new watch** link to add a watch => views/watches/new.html.erb => views/watches/_form.html.erb

•	Click on **Delete this watch** link to delete the watch => controllers/watches_controller.rb => destroy route
1. An alert will display asking **Are you sure you want to delete this watch?**
2. Click **OK** to delete the watch or **Cancel** to abort
3. Deleting the watch will also delete any related join records in the complications_watches join table

•	Click on **Show all of my watches** link to redisplay the initial home page

 **Navbar Links**

•	**My Watch Collection**
   Redisplays the initial home page

•	The signed in ID (not a link)

•	**Sign Out**
   Exits the application

•	**Watch Education**
   Links to a website with information on “Everything You need To Know About Watches”

•	**Watches Online**
   Links to a website that sells watches

* **Twitter**
* **Facebook**
* **Google Plus**

