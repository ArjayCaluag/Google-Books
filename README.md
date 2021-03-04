# **React Portfolio**

This project is a react based Google Books Search App with the use of the Google Books Api. This This project contains multiple components, the use of Node, express, and MongoDB that allows the user to store books of their choice.

<br><br>

![GoogleBooks](https://user-images.githubusercontent.com/52800632/109890125-96cf1300-7c3b-11eb-9a95-ba1b0c575a60.gif)





# **Installation**

Run this command to create your react based application.

```html

npx create-react-app <appname>

```

# **Built With**

<ul>
    <li> React - JS library for building interactive user inferfaces
    <li> Bootstrap - CSS framework
    <li> Javascript - scripting language that allows implementation of complex web features
    <li> Express- Node.js web application framework
    <li> MongoDb - source-available cross-platform database program </li>
</ul>

# **Code Snippet**
Here is a snippit of the use of React Router that is used to render the different pages with components.

```js
 
import React from "react";
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
import "./App.css";
import Saved from "./Components/Saved";
import Search from "./Components/Search";

function App() {
  return (
    <Router>
      <Switch>
        <Route exact path={["/search", "/"]} component={Search} />
        <Route exact path="/saved" component={Saved} />
        <Route exact path="*" component={Search} />
      </Switch>
    </Router>
  );
}

export default App;


```
This snippit showcases the implementation of the google books API
```js
router.get("/google", function (req, res) {
  console.log("Backend req variable:", req.query.q);
  
  let url = "https://www.googleapis.com/books/v1/volumes?q=";
  let query = req.query.q;
  let key = "&key=AIzaSyByK7dx9Q35o7iCatSUJ3_6so-bMZrZq0k";
  axios.get(url + query + key)
    .then(({ data: { items } }) => {
      let specificData = items.map(bookObj => {
        const bookImg = (bookObj.volumeInfo.imageLinks === undefined ? "" : `${bookObj.volumeInfo.imageLinks.thumbnail}`);

        let parsedBook = {
          title: bookObj.volumeInfo.title,
          authors: bookObj.volumeInfo.authors,
          description: bookObj.volumeInfo.description,
          image: bookImg,
          link: bookObj.volumeInfo.infoLink
        }
        return parsedBook;
      });
      res.json(specificData);
    })
    .catch(err => console.log(err));
});



```
# **Deployed Link**

https://googlebooks-rc.herokuapp.com/
# **Authors**

Ron-Arjay Caluag<br>
[Linkedin](https://www.linkedin.com/in/ron-arjay-caluag-00b29b182/)<br>
[Github](https://github.com/ArjayCaluag)

Rand Hale<br>
[Github](https://github.com/prophetrandl)
<br><br>
Sammy Kroner<br>
[GitHub](https://github.com/sammyk118)

The MIT License (MIT)

Copyright (c) 2011-2020 Twitter, Inc.

Copyright (c) 2011-2020 The Bootstrap Authors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
