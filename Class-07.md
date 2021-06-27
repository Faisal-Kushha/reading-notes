# Class-07

## Domain modeling
It is used to generate a model in coding for a certain problem. The model should describe all the different entities along with their attributes and behaviors. In addition to the problem domain constraints. Each entity that stores value in properties and translatethe behavior in method is known as an `Object Oriented Model`.

[Tips](https://github.com/codefellows/domain_modeling#domain-modeling) to follow when building your own domain models:

1. When modeling a single entity that'll have many instances, build self-contained objects with the same attributes and behaviors.
2. Model its attributes with a constructor function that defines and initializes properties.
3. Model its behaviors with small methods that focus on doing one job well.
4. Create instances using the new keyword followed by a call to a constructor function.
5. Store the newly created object in a variable so you can access its properties and methods from outside.
6. Use the this variable within methods so you can access the object's properties and methods from inside.

--------------
## JavaScript 
In order to create an object you have to use `new` keyword and the object constructor will create an empty object after that you could fill it with the properties and methods. You could also create Objects form the same type by calling the constructor function with the `new` keyword.

Updating the value of properties you have to use dot notation or square brackets. If you want to delete a property you could use `Delete`keyword. Additionally ou can use `Objects` as an `Arrays` and vice versa.

###  Bulit-In Object 
Bulit-In Object have three main group which is as the following:

1. `THE BROWSER OBJECT MODEL`

![BOM](https://flylib.com/books/4/357/1/html/2/files/10fig03.gif)



2. `THE DOCUMENT OBJECT MODEL`

![DOM](https://simplesnippets.tech/wp-content/uploads/2018/10/what-is-document-object-model-in-JS-featured-image.jpg)

3. `GLOBAL JAVASCRIPT OBJECTS`

![GJO](https://www.learnsimpli.com/wp-content/uploads/2019/09/javascript-data-types.png)

---------------
## HTML 
In order to create a table in HTML and adding it to the webpage you have to use `<table>`element. The table is consist of rows and each row is created with the `<tr>` element and each row have a number of cells which refrered to by `<td>` element.

![table](https://docs.nomagic.com/download/attachments/36311706/HTML%20tag%20for%20fragments%20of%20table.png)
