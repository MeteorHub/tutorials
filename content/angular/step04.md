{{#template name="angular-step04"}}

# Adding tasks with a form

In this step, we'll add an input field for users to add tasks to the list.

First, let's add a form to our HTML:

{{> DiffBox tutorialName="simple-todos-angular" step="4.1"}}

Here's the JavaScript code we need to add to listen to the `submit` event on the form:

{{> DiffBox tutorialName="simple-todos-angular" step="4.2"}}

Now your app has a new input field. To add a task, just type into the input field and hit enter. If you open a new browser window and open the app again, you'll see that the list is automatically synchronized between all clients.

### Attaching events to templates

As you can see, this is just a regular Angular application.

In our case above, we are listening to the `submit` event on our form to call the `addTask` controller function.

### Inserting into a collection

Inside our controller function, we are adding a task to the `tasks` collection by simply calling `Tasks.insert()`. We can assign any properties to the task object, such as the time created, since we don't ever have to define a schema for the collection.

Being able to insert anything into the database from the client isn't very secure, but it's okay for now. In step 9 we'll learn how we can make our app secure and restrict how data is inserted into the database.

### Sorting our tasks

Currently, our code displays all new tasks at the bottom of the list. That's not very good for a task list, because we want to see the newest tasks first.

We can solve this by sorting the results using the `createdAt` field that is automatically added by our new code.
Until now you probably used Angular sort filter to do so. you can still use that here, but we are going to use a different method because it is better for real world use cases.

Replace the `Tasks` collection variable with a function inside our `tasks` helper.
The function will return a the result of calling the `find` function with the `sort` parameter on our `Tasks` collection, like that:

{{> DiffBox tutorialName="simple-todos-angular" step="4.3"}}

To better understand the difference between using the sort filter and the collection options, check out the advanced tutorial about [search, sort and pagination](http://angular-meteor.com/tutorial/step_12).

In the next step, we'll add some very important todo list functions: checking off and deleting tasks.
{{/template}}
