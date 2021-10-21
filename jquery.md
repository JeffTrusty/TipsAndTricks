# JQuery

## Add JQuery before your application code that will use it

```HTML
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<!-- My app -->
<script src="app/app.js" defer></script>
```

## Using JQuery

Use the $ symbol for JQuery

```JavaScript
// Using the css method will either set (2 parameters) or get (1 parameter)
// Set the h1 font-size to 5rem:
$("h1").css("font-size", "5rem");
// get the h1 font-size:
var h1FontSize = $("h1").css("font-size");

// Similar to css classes, you can get (1 parameter) or set (2 parameters) HTML object attributes
// get the h1 class(s)
var h1Classes = $("h1".attr("class"))
// change the link of all anchor tags
$("a").attr("href", "https://www.yahoo.com");
```

## Changing the text / innerHTML of an objects

```JavaScript
$("h1").text("bye"); // .text method changes all h1 objects text to "bye"
$("button").html("<em>click me</em>"); // .html method changes all button objects to show "click me" and apply the emphasized to them
```

## Add click event listener to all buttons

```JavaScript
$("button).click(function() {
  $("h1").css("color", "purple"); // change the h1 text-color to purple on click of any button
});
```

### Best Practice

Add multiple styling classes to objects
Create class1Name and class2Name classes in your CSS file and then add / remove the classes to the objects

```JavaScript
// adds class1Name and class2Name to all h2 objects
$("h2").addClass("class1Name class2Name");
$("h2").removeClass("class1Name class2Name");
```

