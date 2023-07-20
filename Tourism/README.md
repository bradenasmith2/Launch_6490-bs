# Week 3 Assessment

### Setup
* In Package Manager Console
* `drop-database` and then >
* `update-database` >

## Exercise

Your goal for this assessment is to have an application that allows a user to do the following:
* Create a State by submitting a Form >
* See all the cities for a specific state (city index page) >
* Create a City for a State by submitting a form >

### Creating a State (3 points)

Update the application so that a user can create a State by submitting a form. >
* You will need to thoroughly test this functionality. >
* Do not break any currently passing tests.

### City Index Page (3 points)

Update the application so that a user could visit "/states/1/cities" to view all of the cities for a state (in this case, the state with id 1). >
* You will need to thoroughly test this functionality. >
* Do not break any currently passing tests.

### Create a City (9 points)

Update the application so that the pre-existing CityCRUD tests will pass. >
* There is some starter code that is not yet working.
* You may change any code in the Controllers, Views, and Models.
* You may NOT change the pre-existing tests. >

## Questions (5 points)

Edit this file with your answers.

1. Create a Diagram of the Request/Response cycle that would occur when a user creates a city.  Include as much detail as possible!  **Send and image/screenshot of your diagram to your instructors via slack.** (2 points)
    * https://gyazo.com/0de33f99262cb54047c8f70374869a27

2. How does a form submission know what request should be made? Use examples.
    * When we are making our form in the view, we must specify the method(request).
    * For example, if I'm making a form to add a new car, it could be: <form id="new-car-form" *method="post"* action="/cars">
        * This is then handed to the controller action that has been labeled [HttpPost] typically a Create().

3. Imagine you are explaining how to create a resource to a co-worker.  How would you describe how the controller action `Create` works?
    * The Create action is how we actually add the form data into our database. Just above where we define our action Create(), we specify that this action is a [HttpPost].
        * Now that the action knows its a post request, we can accept the object created by the form(the input "name" field HAS to match our property in models), for example our car from earlier and add that to our context (database) and save it.
        * From here, it is common to then redirect the user to that new car's page, with Redirect("/car/:id")

4. In our State creation functionality - what would happen if a user did not enter an Abbreviation before submitting the form?
    * Since Abbreviation is a required field for our object to be created, if the user does not enter one then the object would not be created.
        * Since the object would not be created, when the user is redirected to that objects page, they would get an error stating that page does not exist, and the developer would get a 'object reference is not set' error.
            * The program breaks in the [HttpPost] Index action when attempting to SaveChanges(), but since a non-null field IS null, it cannot be saved.


## Rubric

This assessment has a total of 20 points.  A score of 15 or higher is a pass.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
