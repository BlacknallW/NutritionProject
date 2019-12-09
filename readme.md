# MyVitaLog
Website designed to help users log and keep track of their nutritional intake, as well as learn about the nutrients that are going into their bodies.

## API Calls

### FDA API https://fdc.nal.usda.gov/api-guide.html#food-detail-endpoint
This project uses the FDA's official API for food and nutritional data, which probably explains why the API itself is disorganized and highly redundant. The way this api works is that by default, you're going to need to use two endpoints, one to call the query search for the food items you're looking for, and another to actually get the nutritional information of a specific item using its ID, given by the initial endpoint. One problem that arose due to the upkeep (or lack thereof) of this api is that many entries were completely empty, and others were used several times with varying caloric and nutritional information. To get rid of empty entries, information is only pulled from the database if the food entry isn't empty.

We found a better API down the line, but we were less than 24 hours from launch so there was no time to pivot.

## Database Usage
For this project we used NodeJS with an express server connected to a Postgres server through the PG-Promise npm module. Users were logged in one database, while their food logs were logged in another, connected by the user's ID. The goal was to have users be able to track their progress over the course of the week, but the functionality of allowing any food logs to show up other than the current day was not added, as time ran out.

## Encryption
Passwords! Yes, any system where you can log in will of course require the creation and usage of a password. For user peace-of-mind, we used the Bcrypt npm module to make sure that no one would be able to see the passwords of users, as even we ourselves are unable to see it. When users create an account with a password, the password is automatically run through the encryption method before it's even saved to the database. More than likely, there are still ways to get the user's login information, but we're not able to do it ourselves, and we don't know what we don't know, so the best bet is just to advise users not to use a password they use across multiple sites, and we haven't really promoted the site or anything, nor do we intend to.

## Styling
This is the portion of the project that I was directly responsible for. I chose to use BulmaCSS for styling because styling frameworks save a lot of time, and therefore money. I used a green and white color scheme because when I think of "health and wellness", I think of bright colors like green and white. Most of the site layout uses a tiling system for symmetry, and somewhat compartmentalizes all of the information on the website. There are still issues with scaling when the user is using a large monitor, however.
