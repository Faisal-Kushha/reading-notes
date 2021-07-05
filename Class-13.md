# Class-13
Local storage lets a site save up to 5 MB of data to a user's computer. That data can be accessed using JavaScript from any other page on the same site. That data lasts between visits and after the browser has closed. With session storage, the data disappears when the browser window is closed.

Cookies were invented early in the web’s history, and  they can be used for the local storage of small amounts of data. However they have three disadvantages:

1. Cookies are included with every HTTP request.

2. Cookies are included with every HTTP request.

3. Cookies are limited to about 4 KB of data — enough to slow down your application.

![storage](https://i.stack.imgur.com/cI5kT.jpg)

### HTML5

![html5](https://techglimpse.com/wp-content/uploads/2013/04/localstorage.jpg)

LocalStorage is an HTML5 web storage object for storing data locally on user’s computer. Data stored locally has no expiration date and will exist until it’s been deleted. 


HTML5 local storage is part of the Web storage application. It is a method by which Web pages locally store named key/value pairs inside a client's Web browser. Similar to cookies, this saved data exists even when you close a browser tab.

Track storage area changes can be by trap the storage event. The storage event is fired on the window object whenever `setItem()`, `removeItem()`, or `clear()` is called and actually changes something.