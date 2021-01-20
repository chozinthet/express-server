# express-server

- express routes 

- express catch post-input from html file

- express static file

npm packages --> express, body-parser

```
public 
      home.html
      index.html
      style.css
server.js
```

server.js

```
const express = require('express');
const bodyParser = require('body-parser');
const app = express();

app.use(bodyParser.urlencoded({ extended: false }));
app.use(express.static(__dirname + '/public'));

app.get('/', (req, res) => {
  res.sendFile(__dirname + "/index.html");
});

app.get('/home', (req, res) => {
  res.sendFile(__dirname + "/home.html");
});

app.post('/', (req, res) => {
    console.log(req.body.name);
    res.send('inputing complete')
})

app.listen(3000, () => {
  console.log(`Example app listening at http://localhost:3000`)
})
```

public/index.html

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
    <link rel="stylesheet" href= "style.css">
</head>
<body>
    <form action="/" method="post">
        <input type="text" name="name">
        <button type="submit" class="btn">Submit</button>
    </form>
</body>
</html>
```

public/home.html

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
    This is Home
</body>
</html>
```

public/style.css

```
.btn{
    background-color: blue;
    color: #fff;
    outline: none;
    border: none;
}
```
