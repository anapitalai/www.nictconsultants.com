---
title: Web Application Development
author: Alois Napitalai
date: '2018-07-12T13:34:19+10:00'
image: /images/webworks.png
---
### Web Application Tutorial for GDG Lae Participants
##### Abbreviations and Definitions
* 1. Function is group of statements that perform a certain task.
* 2. An object is a real world thing that can be represented in a   program.Custom functions can be created and too there are many
   built-in functions available javascript.
* 3. When a function is created in an object, it is called a
   METHOD.
* 4. A variable is temporary storage in memory of the computer that
   is used to hold data of a certain datatype.
* 5. Some datatypes in js are booleans,string,integers(numbers),ect.
* 6. An eventlistener is a function that listens for a event to take
   place before it is triggered.Some examples are
   input,mouseover,keyup,etc.In our app,we will be using the input
   event. So when data is typed into a input box, a certain function
   is triggered.
* 7. Syntax is the grammar of programming in javascript.

<hr>

* 1. Go to the documents directory and make a folder
loan_calculator
* 2. Start up visual code editor
* 3. Open the folder you made in step 1.You should be staring at a
blank folder.
* 4. Make a folder structure as shown below; <br>
loan_calculator→ <br>
  js→app.js <br>
  images→bg.jpg<br>
  index.html<br>

* 5. Type out the html structure in index.html.

```
<html>
<head>
<title>Loan Calculator App</title>
</head>
<body>
<h1>Loan Web App Calculator</h1>
<div>Content goes here</div>
</body>
</html>

```

* 6. What we have just typed is the basic structure of an html page.
* 7. The actual app content will be in the div element which is the
only div element in the structure. We wont be making this too
complicated, we will keep it as simple as possible.
* 8. Bring up the terminal in vsc by pressing ctrl + `.
* 9. What we will be doing now is starting up our local web server
from the terminal to see what our app looks so far.
* 10. Type lite-server <Enter>.
This should start up the web server making the html you have
put together show in the web browser.
* 11. Our next task is to style our app.In the style.css file, add
the contents below.  <br>
```
body,html{
margin:0;
padding:0;
font-size:16px;
height:100%;
width:100%;
background-image:url(‘/images/bg.jpg’);
background-repeat:no-repeat;background-size:cover;
background-positon:center;
}
```
* 12. To style the div tag, we have to give a unique identifier to
the element so that we can target it directly with css code. If we
use the div tag as an identifier, that will be universal to the app
so if later we decide to add another div element, that element
will have the save styling applied to it. In this case we have to
give it a class name which will be the unique identifier. Use the
class attribute. Our div element should now look like below.

```
<div class=’main’></div>
```
* 13. The same will also be done to the h1 element. But for the
h1 we will use an id attribute. It should now look like below.

```
<h1 id=’heading’>Loan Web App Calculator</h1>
```

* 14. Append the style rules to the style.css file.
<br>
```
.main{
margin:10px;
padding:10px;
background:#111;
font-size:17px;
}
#heading{
margin:10px;
padding:10px;
background:#111;
}
```
* 15. You should notice the styling are not applied because we
have not linked the stylesheet to our html file. Now it is time
do that,go to the head element and add;<br>
```
<link type=’text/stylesheet’ src=’/css/style.css’>
```
16. Add a form with as shown below with all the attributes shown.
Take note of the from-group which is applied to all div
elements applying the same styling to all.
```
<form>
<div class="form-group">
<label for="gross">Loan Amount</label>
<input name="grossInput" value="500" type="number">
</div>
<div class="form-group">
<label for="fortnights">Fortnights</label>
<input name="fortnightInput" value="10"
type="number">
</div>
<div class="form-group">
<label for="interest">Interest</label>
<input name="interestInput" value="2.4"
type="number">
</form>
```
* 17. Also add a div element after the form that will be used to
display the calculated values.
```
<div class=”display”>00.00</div>
```
* 18. Add a styling to the display class in the styles.css file
```
.display{
margin:20px;
fon-size:30px;
}
```
* 19. After all is done,we are ready to add interactions making the app
come to life by using js. Firstly we need to make a reference to all
the input and display elements in the app.
<br>
```
var grossInputHandle=document.querySelector([name=grossInput]);var fniteInputHandle=document.querySelector([name=fniteInput]);
var
interestInputHandle=document.querySelector([name=interestInput]);
var displayViewHandle=document.querySelector([‘.display’]);
```
* 20.create the function so that when there is a change in any of the
input fields, it is triggered automatically.
```
function calculate(){
var grossValue = grossInputHandle.value;
var fniteValue=fniteInputHandle.value;
var interestValue=interestInputHandle.value;
var result = grossValue * fniteValue * interestValue;
displayViewHandle.innerText=’PGK’ + result
}
```
* 21.Add the eventListeners.When there is a change in the value in the
inputgrossInputHandle.addEventListener(‘input’,calculate); box the
calculate function is triggered.
```
grossInputHandle.addEventListener(‘input’,calculate); 
fniteInputHandle.addEventListener(‘input’,calculate);
interestInputHandle.addEventListener(‘input’,calculate);
```
* 21. When a decimal result is obtained, it gives so many place values,
we can restrict that values to two decimal places by adding;
```
result.toFixed(2);
```
* 22. For the above to work we need to the add the app.js to the
index.html file just before the closing body tag.

```
<script src=’js/app.js’></script>
</body>
```