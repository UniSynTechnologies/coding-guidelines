[Back to index](https://github.com/UniSynTechnologies/coding-guidelines)

## Concepts
When possible, use a preexisting style rule or function instead of recreating the wheel by making your own. The chances that what you are trying to achieve has been done in some form already are pretty high.

Unless you see obvious violations of your team's guidelines, it is generally bad practice to go through existing code making changes to fit your personal coding style. This results in long and hard to read commits while reviewing code changes due to unnecessary line changes. The preferred method is to bring up coding style preferences to the team and discuss if they should be included in the shared standard before making changes.

Code you add to a project should matches the style of the code surrounding it regardless of your personal style. Code jumping between styles reads something like a message written by 5 different people with 5 different styles. "Hello fine m8 or madam, wot u doin? Holla at me in the decline of day when thou art prepared for din din." Not pleasant to read nor easy to understand.

## Naming

Variable, function, and object class names should use camelCase with the first word lowercase and following words connected without space and capitalized.

CSS class names should be lowercase and separated by dashes.

File names should use camelCase with the exception of adding a dash separated sub category of the file. Example would be siteSettings-service.js where siteSettings is what it is about and service is the sub category of the file.

Don't unnecessarily abbreviate names. Saving a couple characters by removing vowels is not worth the loss in readability. Your code should be named clearly enough that comments are not entirely necessary because the names speak for themselves.

A great rule to go by: “if the code is so unclear that it requires a comment, then maybe it should be rewritten instead”. An important sign of a good developer is comments: their presence and even their absense.

The following code is "self-descriptive" and requires no comment because it is clear what it does.
```javascript
getCookedBacon();

function getCookedBacon() {
    var bacon = getBacon();
    var pan = getPan();
    pan.contents.push(bacon);

    var heatedPan = addHeat(pan);

    return heatedPan.contents;
}

function addHeat(object) {
    object.temperature += 400;
    for (var i = 0; i < object.contents.length; i++) {
        object.contents[i].temperature = object.temperature;
    }

    return object;
}
```

## Code Style
Try to keep lines below 120 characters long. This is a reasonable length on the average 1920x1080 monitor before word wrap kicks in.

Keep ternary conditions on the same line. If you think it needs multiple lines then it should be a normal condition with if else and curly bracers "{}".

For HTML elements with many attributes resulting in a long line, it is a good practice to break them into multiple lines per attribute with the first attribute remaining inline with the element itself like so:
```html
<a href="https://www.unisyntechnologies.com"
   class="homepage-link"
   id="our-homepage">Home</a>
```
As also seen above, for inline elements such as span or a links, it is generally best to keep their contents inline with the tag itself. For div tags or other block level elements, it is preferred to make a new line and indent the contents like so:
```html
<div>
    Hey look at me!!
</div>
```
This assists with readability of the hierarchy of the code while also allowing you to easily guess what the page being generated will look like based on the flow and new lines in the code.

All files should have 1 blank line at the end of the file. Lots of discussion about this general "rule" here: https://stackoverflow.com/questions/729692/why-should-text-files-end-with-a-newline but it really comes down to being because some text parsers only could lines ending in new line characters are actual lines to parse. So if our code is ever passed through a 3rd party parser for minification or uglification or some other automated process there is a slight chance this could be a problem.

![](https://s3.amazonaws.com/unisyn-wp-assets/wp-content/uploads/2018/02/02234458/coding-style-1.png)
![](https://s3.amazonaws.com/unisyn-wp-assets/wp-content/uploads/2018/02/02234501/coding-style-2.png)
![](https://s3.amazonaws.com/unisyn-wp-assets/wp-content/uploads/2018/02/02234502/coding-style-3.png)
