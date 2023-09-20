

# Set up Structure

 ## 1. Pre setting 
    Make sure have Node.js and npm installed on your VPS.

    ```
    Copy code
    sudo apt update
    sudo apt install nodejs npm
    sudo apt install git
    mkdir my-prompt-search
    cd my-prompt-search

    ```
## 2. Set up Project Structure

Create the following directories and files to mimic the structure of the original repository:
- `template/`
  - `js/`
    - `index.js`
    - `copy-to-clipboard.js`
  - `partial/`
    - `footer.ejs`
    - `header.ejs`
  - `styl/`
    - `index.styl`
  - `widget/`
    - `search.ejs`

### Install Required Packages
1. Initialize a new Node.js project.
   ```bash
   npm init -y
   ```

2. Install Express, EJS, and other required packages.
   ```bash
   npm install express ejs stylus
   ```

## 3. Implement the Backend
1. Create an `app.js` file at the root of your project.
This file will serve as the entry point for your application.

#### Import Required Modules

At the top of `app.js`, import the required Node.js modules.

```javascript
const express = require('express');
const path = require('path');
const ejs = require('ejs');

const app = express();

// Set EJS as the template engine
app.set('view engine', 'ejs');

// Set static and views directories
app.use(express.static(path.join(__dirname, 'template/js')));
app.set('views', path.join(__dirname, 'template/partial'));

// Define routes
app.get('/', (req, res) => {
  res.render('index', { title: 'Prompt Search' });
});

// Start the server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

```

#### Initialize Express App

Initialize an Express application and set it to use EJS as the template engine.

```javascript
const app = express();
app.set('view engine', 'ejs');
```

#### Set Static and Views Directory

Specify the directories for your static files (JavaScript, CSS, images, etc.) and EJS templates.

```javascript
app.use(express.static(path.join(__dirname, 'template/js')));
app.set('views', path.join(__dirname, 'template/partial'));
```

#### Define Routes

Define a route to render your main page. For now, let's assume you have a file named `index.ejs` in your `template/partial` directory.

```javascript
app.get('/', (req, res) => {
  res.render('index', { title: 'Prompt Search' });
});
```

#### Start the Server

Finally, start the Express server on a specific port. For example, let's use port 3000.

```javascript
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

#### Complete `app.js`

Putting it all together, 

Once you've created this file, you can run your application with the following command:

```bash
node app.js
```

 should be able to access it at `http://localhost:3000`.



## Step 4: Implement the Frontend

#### 4.1 Create EJS Templates

First, let's create the EJS templates for the header, footer, and search widget. These will go in the `template/partial` directory.

- `header.ejs`: This file will contain the HTML code for the header section of your website.
  
  ```html
  <!DOCTYPE html>
  <html>
  <head>
    <title><%= title %></title>
  </head>
  <body>
    <header>
      <h1><%= title %></h1>
    </header>
  ```

- `footer.ejs`: This file will contain the HTML code for the footer section of your website.

  ```html
    <footer>
      <p>Copyright 2023</p>
    </footer>
  </body>
  </html>
  ```

- `search.ejs`: This file will contain the HTML code for the search widget.

  ```html
  <div id="search-widget">
    <input type="text" id="search-box" placeholder="Search for prompts...">
    <button id="search-button">Search</button>
  </div>
  ```

#### 4.2 Create Main Index EJS File

Create an `index.ejs` file in the `template/partial` directory. This file will include the header, footer, and search widget templates.

```html
<%- include('header') %>
<main>
  <%- include('search') %>
</main>
<%- include('footer') %>
```

#### 4.3 Populate JavaScript Files

Next, let's populate the JavaScript files in the `template/js` directory.

- `index.js`: This file will contain the main JavaScript logic for your application.

  ```javascript
  document.addEventListener("DOMContentLoaded", function() {
    const searchButton = document.getElementById("search-button");
    searchButton.addEventListener("click", function() {
      // Implement search logic here
    });
  });
  ```

- `copy-to-clipboard.js`: This file will contain the JavaScript code to copy text to the clipboard.

  ```javascript
  function copyToClipboard(text) {
    const textarea = document.createElement("textarea");
    textarea.value = text;
    document.body.appendChild(textarea);
    textarea.select();
    document.execCommand("copy");
    document.body.removeChild(textarea);
  }
  ```

That should give you a good starting point for the frontend. Once these files are created, your frontend should start taking shape. You can run your server and navigate to `http://localhost:3000` to see the changes.




## Step 5: Styling with Stylus

#### 5.1 Install Stylus Middleware

First, install the Stylus middleware for Express to compile Stylus files into CSS on the fly.

```bash
npm install stylus
```

#### 5.2 Update `app.js`

Add the Stylus middleware to your `app.js` file to compile Stylus files.

```javascript
const stylus = require('stylus');

// Add this line to your existing app.js
app.use(stylus.middleware(path.join(__dirname, 'template/styl')));
```

#### 5.3 Create Stylus File

Create a new file named `index.styl` in the `template/styl` directory. This file will contain the Stylus code for styling your application.

Here's a simple example to get you started:

```stylus
// Basic styling for header
header
  background-color #f2f2f2
  text-align center
  padding 1em

// Styling for search widget
#search-widget
  margin 2em auto
  width 80%

#search-box
  width 70%
  padding 0.5em

#search-button
  width 20%
  padding 0.5em
  background-color #007bff
  color white
```

#### 5.4 Link Compiled CSS

In your `header.ejs`, add a link to the compiled CSS file. The Stylus middleware will compile `index.styl` to `index.css` in the same directory.

```html
<head>
  <title><%= title %></title>
  <link rel="stylesheet" href="/index.css">
</head>
```

#### 7.5 Test Your Styles



## 
G: The existing code is designed to read Markdown files from a given directory, extract certain pieces of information from each file, and then create a JSON object that holds this information. The code is tailored for a specific format of Markdown files, which are expected to represent Linux commands.

To make this code more flexible and accept names that are not Linux commands, you can make a few modifications:

### Modifications:

1. **Flexible Title Matching**: Instead of strictly looking for Linux command names, you can make the title matching more flexible.

2. **Error Handling**: Add more robust error handling to deal with cases where the expected format is not met.

Here's how you can modify the `createDataJSON` function:

```javascript
function createDataJSON(pathArr) {
  return new Promise((resolve, reject) => {
    try {
      const commandData = {};
      const indexes = [];
      pathArr.forEach((mdPath, i) => {
        const json = {}
        const con = FS.readFileSync(mdPath);
        const str = con.toString();
        let title;

        // Try to match the title based on the existing format
        const titleMatch = str.match(/[^===]+(?=[===])/g);
        if (titleMatch && titleMatch[0]) {
          title = titleMatch[0].replace(/\n/g, '').replace(/\r/, '');
        } else {
          // If the title doesn't match the expected format, use the file name as the title
          title = path.basename(mdPath, '.md');
        }

        // Command or Prompt Name
        json["n"] = title;
        // Command or Prompt Path
        json["p"] = `/${path.basename(mdPath, '.md').replace(/\\/g, '/')}`;

        // Command or Prompt Description
        let des = str.match(/\n==={1,}([\s\S]*?)##/i);
        if (!des) {
          throw `Invalid format: ${mdPath}`;
        }
        des = des[1] ? des[1].replace(/\n/g, '') : des[1];
        des = des.replace(/\r/g, '')
        json["d"] = des;

        indexes.push(json);
        commandData[title] = json;
      });
      resolve({
        json: commandData,
        data: indexes
      });
    } catch (err) {
      reject(err);
    }
  });
}
```

In this modified version, if the title doesn't match the expected format (i.e., followed by `===`), the code will use the file name as the title. This should make the code more flexible and allow it to handle a wider range of "command" or "prompt" names.

##  Install package

creating a GitHub Action to automatically generate a Table of Contents (ToC) in your README file using the markdown-toc
npm install -g markdown-toc
then write a generate.yml in .github/workflow
```
name: Generate Table of Contents

on:
  push:
    paths:
      - 'README.md'

jobs:
  generate-toc:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Setup Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'

    - name: Install markdown-toc
      run: npm install -g markdown-toc

    - name: Generate ToC
      run: markdown-toc -i README.md

    - name: Commit changes
      run: |
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        git add README.md
        git commit -m "Automatically update ToC" || echo "No changes to commit"
        git push
```

