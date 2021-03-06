{{#template name="blaze-step02"}}
# Defining views with templates

To start working on our todo list app, let's replace the code of the default starter app with the code below. Then we'll talk about what it does.

First, let's remove the body from our HTML entry point (leaving just the `<head>` tag):

{{> DiffBox tutorialName="simple-todos" step="2.1"}}

Then we create some new files in the `imports/` directory:

{{> DiffBox tutorialName="simple-todos" step="2.2"}}

{{> DiffBox tutorialName="simple-todos" step="2.3"}}

Files inside `imports/` only load if they are imported, so we'll need to import `imports/ui/body.js` from our frontend JS entrypoint (`client/main.js`---note that we remove the rest of the code from this file):

{{> DiffBox tutorialName="simple-todos" step="2.4"}}

You can read more about how imports work and how to structure your code in the [Application Structure article](http://guide.meteor.com/structure.html) of the Meteor Guide.

In our browser, the app will now look much like this:

> #### Todo List
> - This is task 1
> - This is task 2
> - This is task 3

Now let's find out what all these bits of code are doing!

### HTML files in Meteor define templates

Meteor parses HTML files and identifies three top-level tags: **&lt;head>**, **&lt;body>**, and **&lt;template>**.

Everything inside any &lt;head> tags is added to the `head` section of the HTML sent to the client, and everything inside &lt;body> tags is added to the `body` section, just like in a regular HTML file. 

Everything inside &lt;template> tags is compiled into Meteor _templates_, which can be included inside HTML with `{{dstache}}> templateName}}` or referenced in your JavaScript with `Template.templateName`.

Also, the `body` section can be referenced in your JavaScript with `Template.body`. Think of it as a special "parent" template, that can include the other child templates. 

### Adding logic and data to templates

All of the code in your HTML files is compiled with [Meteor's Spacebars compiler](https://github.com/meteor/meteor/blob/devel/packages/spacebars/README.md). Spacebars uses statements surrounded by double curly braces such as `{{dstache}}#each}}` and `{{dstache}}#if}}` to let you add logic and data to your views.

You can pass data into templates from your JavaScript code by defining _helpers_. In the code above, we defined a helper called `tasks` on `Template.body` that returns an array. Inside the body tag of the HTML, we can use `{{dstache}}#each tasks}}` to iterate over the array and insert a `task` template for each value. Inside the `#each` block, we can display the `text` property of each array item using `{{dstache}}text}}`.

In the next step, we will see how we can use helpers to make our templates display dynamic data from a database collection.

{{> addingCSS cssFileName="simple-todos.css"}}

{{/template}}
