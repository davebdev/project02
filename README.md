# A-Lister

A-Lister (working title) is an online 'to-watch' list keeper. A-Lister is a flask python app supported by a postgreSQL database, hosted on [github](https://github.com/davebdev/project02) and using heroku to deploy at [https://enigmatic-caverns-29903.herokuapp.com/](https://enigmatic-caverns-29903.herokuapp.com/). A-Lister uses an API developed at [The Movie DB](https://www.themoviedb.org/documentation/api) to supply all the movie data.

This has been created for Unit 2 of the General Assembly Software Engineering intensive (remote flex), cohort 08. This unit has been my first foray into Python.

## Database design

My approach to this app was to first try to get an understanding of the way the database would be structured. In tandem with this, I tried to come up with some wireframes for the pages that would appear, which solidified the user flow through the app, and also allowed me to amend the database structure to work with my intentions for the app, all before I'd written a single line of code. This approach meant I could properly size the scope of this project and remove a few extra things that I knew I wouldn't have time for in the week I had to build it. Some of the extra features I was hoping to incorporate were:
    - allowing users to 'follow' each other's lists/user pages
    - creating a search for public facing lists
    - a dynamic search bar which filtered results as the user types

The below diagram shows the original structure of the database:

![a lister database structure](static/img/project02_db_structure.png)


### Storing movie data

In the approach to this app, I had a question in my mind about how much movie data to store in the database, considering I would be using an API to retrieve the data first. After a conversation with a colleague, [Chris](https://github.com/Chrispy1987), he suggested that it might be better to store the data needed for the app once the movie was committed to the list. He further explained that you can have a table specifically for the movie data, which the list data could reference by way of a movie id, so that you wouldn't be storing a version of the movie for every user, but rather that each user instance of the movie would draw from the one row in the movie table. He also suggested storing a count so that if the numbr of times that movie got used in various user lists got down to 1 and the final user was deleting the movie from their list, that movie could then also be deleted from the database so as to not take up unnecessary space. All of these ideas were great and I jumped onto them straight away.

The below diagram shows the restructured (v2) version of the database:

![a lister database structure v2](static/img/project02_db_structure_v2.jpeg)



## Wireframes

The following images are basic wireframes built to both illustrate function and page structure, but also serves as a user journey through the app.

### Sign up

![sign up wireframe](static/img/1_sign_up.jpeg)

### Login

![login wireframe](static/img/2_login.jpeg)

### Empty homepage (no lists)

![user homepage without lists wireframe](static/img/3_user_homepage_w_o_lists.jpeg)

### Create new list

![new list page wireframe](static/img/4_new_list_page.jpeg)

### Empty new list

![empty new list wireframe](static/img/5_empty_new_list.jpeg)

### Search for new movies to add

![search for new movies wireframe](static/img/6_search_for_new_movies.jpeg)

### User homepage (logged in) with several lists

![user homepage with lists wireframe](static/img/8_user_homepage_w_lists.jpeg)

### User homepage (not logged in), public facing

![user homepage public view wireframe](static/img/9_user_page_public_view.jpeg)

## BUGS!

- user/list link combo works even when the list doesn't belong to the user. In some instances this would result in user being able to edit other user's lists.
- when editing list items without a 'watched' date, if the date stays empty, an error occurs
- issues with updating list privacy


## TO DO:
- make private lists only show to user
- edit/delete list data
- when logging in/out, go back to the page the person was originally on
- rating: custom list order? / order by rating / by watched date / alphabetically
- User settings page (Update password, email, first name, last name etc)
- Scroll functionality in sidebar
- Scroll functionality in main
- Cookies/Session expiration when closing tab/after a time

## Functions:

- users can create an account linked to a unique username so that their lists can be shared publically
- users can create an unlimited number of lists
- users can choose whether a list is public or private
- users can add any movie to their list, which will display the name, release date, tagline, overview and runtime of the movie
- users can mark when they've watched a film
- users can add notes, a rating and edit their 'watched date' for any film
- users can delete individual films from their lists
