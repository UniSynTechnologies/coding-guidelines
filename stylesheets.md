## Concepts
Try to never define the width of an element in px. If you really really for some actual reason want it to be a certain width then set the elemnt to:
```
width: 100%;
max-width: 900px;
```
That said, you likely shouldnt have to do this. You should set a max width on your entire app container usually around 1200px and the anything inside the app should simply be based on percents.
