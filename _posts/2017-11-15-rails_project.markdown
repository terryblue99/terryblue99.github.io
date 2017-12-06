---
layout: post
title:      "Rails Portfolio Project"
date:       2017-11-15 20:19:16 -0500
permalink:  rails_project
---


My Watch Collection is a re-write of my Sinatra Project and is an app that allows watch collectors to document their collection.  

Being an avid watch collector myself, this was very close to my heart and something I've been wanting to do for a long time but did not have the knowledge with which to accomplish it.  Now, thanks to Flatiron School, I have gained that knowledge and hope to contunually improve my app as I learn more.
 
I decided to follow the 80/20 rule for developing my app (that is; 80% preparation and 20% execution).  I stepped away from my computer for some time and with pencil and paper started to map out the flow of my app in the order I thought would be the most efficient, placing those things which I thought needed to be done first at the beginning.  This, of course, didn't mean that I wouldn't encounter any problems, but I would at least have simplified the bulk of the process by thinking them through before starting to code.  I would also have a clearly laid out plan to follow.

I also decided to use branches to code and test each part of my plan before merging it with the master branch.

Below is the Application Design Plan that I came up with:

```
# Application Design Plan

1. Seed data

    - Users  
    - Watches  
    - Complications  

2. Implement Devise/OmniAuth, using Facebook Sign In

    - Sign Up / Sign In / Sign Out  

3. Navbar

    - Header  
    - Flash Messages  

4. Create models and tables

    - user (Attributes: Devise attributes) => Action # 2  

        devise :database_authenticatable, :registerable,  
         :recoverable, :rememberable, :trackable, :validatable,  
         :omniauthable, :omniauth_providers => [:facebook]  

        has_many :watches  

        Method: @user.watches  

    - watch (Attributes: name, maker, movement, band, model_number, water_resistance, date_bought, user_id)  

         belongs_to :user  
         has_many :complications_watches  
         has_many :complications, through: :complications_watches  

         validates :name, presence: true  
         validates :maker, presence: true  

         Methods: @watch.user / @watch.complications   

    - complication (Attributes: name, description)  

       has_many :complications_watches  
       has_many :watches, through: :complications_watches  

       validates :name, presence: true  
       validates :name, uniqueness: true  
       validates :description, presence: true  

       Method: @complication.watches  

    - complications_watch (Attributes: watch_id, complication_id, complication_description)  

       belongs_to :watch  
       belongs_to :complication  

       (When trying to save a record in the join table  
        it fails with "TypeError - nil is not a symbol nor a string"  
        because there is no "primary key".  
        The problem is solved by adding the following line to the model)  

       self.primary_key = 'watch_id'  

5. Create views

    - users (Devise) => Action # 2  
    - watches  
    - complications  

6. Create controllers

    - users (Devise) => Action # 2  
    - watches  
    - complications  

7. Code basic processing

    - Display all watches on successful Sign In  
    - Create a watch  
    - Show a watch  
    - Edit a watch  
    - Delete a watch  
    - Validation messages  
    - Flash messages  

8. Add complexities

    - Create a new watch with complication/s & join table description/s  
    - Delete a complication  
    - Show a complication's description  
    - Display the most maker and their watches  
    - Nested complication form with custom attribute writer in watch model  
    - Nested complication resource "show" form  
    - Nested complication resource "new" form  
    - Form display of validation errors  
```


