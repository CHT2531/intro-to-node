# Introduction to Node.js and NPM
Node.js is a JavaScript runtime (software that can execute JavaScript code). First you will need to download and install Node.js. 
* Visit https://nodejs.org/en/ .
* Choose the option that is 'recommended for most users'.
* After downloading Node.js, installation should be straightforward.

## A simple example

* In a text editor of your choice, create a new JavaScript file, name it test.js. Enter the following code:

```javascript
console.log("Hello world");
const num=23;
if(num > 10){
    console.log(`${num} is bigger than 10`);
}
```
* If you are using Windows you will probably be using PowerShell to issue commands. If you are a Mac user, you will need to use the Terminal.
>if you aren't familiar with using a Command Line Interface (CLI) you can find an [basic introduction here](../intro-to-using-a-cli.md).
* Using PowerShell navigate to the folder where you have saved *test.js* (or you can use the file explorer to navigate to the folder and then hold down shift and right-click the mouse, you should get an option saying open PowerShell). 
* Using PowerShell enter the command:
```
node test.js
```
* You should see something like the following: 
```
D:\work\CHT2531\intro-to-node>node test.js
Hello world
23 is bigger than 10
```
* As you can see, we have executed JavaScript code without the use of a web browser. 

This example is just to get the idea of executing JavaScript code outside a web browser, we won't actually need to write Node.js programs. Instead we will use programs (packages) that other people have written to help us build our web applications. 

## Node packages
Packages are used by front-end web developers in two ways:
1. Some packages are command line tools that can help us when developing a website. 
2. Some packages are simply libraries that we include in our projects e.g. there is a Leaflet package.

## Using a Node.js command line tool
An example of a command line tool package is a Node.js version of Sass (https://www.npmjs.com/package/sass). We can use this to compile our Sass code. 
* First, download this repository. It features a simple web application built using HTML, Sass, CSS and JavaScript. 
    - Open the website in a text editor and in a browser to check it works ok. 
* In PowerShell open this folder. If you enter ```ls``` you should see the following files and folders listed:
```
    Directory: C:CHT2531\week11\practical


    Name
    ----
    css
    js
    sass
    index.html
    intro-to-using-a-cli.md
    README.md
```
* Using PowerShell enter the following command
```
npm install -g sass
```

> I have specifed -g here. This stands for global. The package will be installed globally i.e. the sass compiler will be available anywhere on my machine not just in this project. 

* In a text editor, from the sass folder open the *style.scss* file.
* Make a change to the RGB values for one of the Sass variables.
* Back in PowerShell enter the following:

```
sass ./sass/style.scss ./css/style.css
```

* This will compile the Sass code into CSS. 
    - You can find a complete list of Sass commands at https://sass-lang.com/documentation/cli/dart-sass. 
* Refresh the page in the browser to make sure you have successfully changed the colour via Sass. 
* There are lots of packages that we can install and use in a similar way e.g. minify(https://www.npmjs.com/package/minify) to minify code, imagemin(https://www.npmjs.com/package/imagemin) to optimise images. 

## Using Node.js to include libraries in our project
The other use of Node.js is to manage the libraries in our project. Before we do this we need to know how to create a Node.js project.

### Creating a Node.js project
* Using PowerShell make sure you are still in the root of this practical work folder i.e. the folder with *index.html* in it. 
* Enter *npm init -y* 
* This will create a *package.json* file with default settings.
* *package.json* is like a configuration file for a Node.js project. Open this in a text editor to see the default settings. You don't need to change any of them for now. 

### Using a JavaScript library
As a simple example we will use the voca library (https://vocajs.com/). Voca is a small library that will allow us to perform simple string manipulations. 
* In PowerShell enter the following command
```
npm install --save voca
```
* You should get some feedback that voca is being downloaded and installed. 

> Previously we would have gone onto the Voca website and downloaded the code (https://raw.githubusercontent.com/panzerdp/voca/v1.4.0/dist/voca.min.js) and then linked to it in our HTML page.
> 
* If you look in the *package.json* file you should see that the dependencies section has updated to include voca.
    - The flag ```--save-dev``` tells Node.js to add the library to the list of dependencies in the *package.json* file. 

```
  "dependencies": {
    "voca": "^1.4.0"
  },
```
* You should also find that you have a new *node_modules* folder in your project and inside here there should be a voca folder.  
* Open *app.js* change the code to use the Voca libary

```
import voca from '../node_modules/voca/index.es2015.js';
const testString = 'This is a simple string to test Voca'
console.log(voca.snakeCase(testString))
```
* This uses an ES2015 import statement to use the Voca library. 
* Refresh the page in a browser. Open the console to make sure this has worked. 
* We can install any library in the same way. You just need to find the library on the NPM website (https://www.npmjs.com/). 

### Here are some more points about using Node.js and NPM
* If we need to move the project to a different machine or share it with someone else e.g. via GitHub, we **shouldn't** copy the *node_modules* folder. 
    - Instead the *package.json* file describes the project's dependencies.
    - Someone opening the project on a different machine can simply run
        ```
        npm install
        ```
    - And all the projects dependencies will be downloaded and installed. 

* The approach described here is an improvement on manually downloading library code, but could be improved: 
    * It is a little tedious having to find the right .js file in the library folder i.e. the line that says
    ```
    import voca from '../node_modules/voca/index.es2015.js';
    ```
    * Older web browsers don't support ES2015 Modules so this code won't work in older browsers. 
We can get around these problems by using a module bundler e.g. Webpack. See https://webpack.js.org/guides/getting-started/ for an introductory tutorial.  

## Why --save?
It is important to use the ```--save``` flag when installing packages as it maintains a record of all the packages that are needed to run the application. When sharing the project with someone else or moving it to a different location, typically you won't copy the contents of the *node_modules* folder.  Instead someone will run *npm install* from the root of the project. This will look in the *package.json* file for the list of modules to install. 

There are other commands/settings that are worth knowing about

* The ```--save-dev``` flag. This is used to specify a package that is needed for development but not to run the application e.g. the Sass package we used could be added as a development dependency. 
* ```npm list```. Simply lists the installed local packages.
* ```npm uninstall [package name]```. Uninstalls the specified package. 

## Learning More
Most Node.js information and tutorials on the web are written for people wanting to build server-side applications using Node.js. Here are couple of links that are more focussed on front-end web development and NPM.  
* https://www.agiliq.com/blog/2019/01/using-npm-to-manage-frontend-libraries/
* https://www.sitepoint.com/beginners-guide-node-package-manager/ 

