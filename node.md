# Node Projects

## Setting up a Node Projects

```Powershell
# creates the node_modules folder
npm init
# you will also want to create .gitignore file and add node_modules to the file
```

## Dependencies

- Dependencies that are only needed in non-prod environments should be installed with npm using the --save-dev option
- Dependencies that are needed in all environments should not use the --save-dev option

## Updating Dependencies

```Powershell
# Yellow entries are for packages that have been updated, but are not allowed in your package.json file
# Red entries are for packages that have updates and are allowed by your package.json file
npm outdated
# update packages that can be safely updated (red)
npm update
# to update yellow packages you need to install the latest version of the package with the @latest option
npm install express@latest
# NOTE: you may need to make changes to your code

# Displays vulnerabilities and how to resolve them
npm audit
# Updating to resolve vulnerabilities
npm audit fix
npm audit fix --force
```

## Setup Node as an API Server

```Powershell
npm install express
npm install cors
npm install body-parser
npm install -g nodemon
npm install mongoose // installs mongoose DB package to help with accessing Mongo databases
```

## Basic Node Server Setup

```Powershell
const express = require('express');
const cors = require('cors');
const bodyParser = require('body-parser');

const port = process.env.port || process.env.PORT || 5000;

const app = express();
//configure app
app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());
app.use(cors({ orgin: /http:\/\/localhost/}));
app.options('*', cors());


app.listen(port, () => {
  console.log(`Server on port ${port}`);
});
```
