# README

Natours Project

Completed by: Alex Zonis

See website: [https://alikzi.github.io/SASS-project-1/](https://alikzi.github.io/SASS-project-1/)

## Description

It is a website for a fictional company that offers tours in the nature. It is a project for “Advanced CSS and SASS” course from Udemy created by Jonas Schmedtmann. The course provided the design and code samples. Successful completion of the project requires knowledge and skills in areas of web development that I summarized and detailed here in the sections that follow.

- _Setting CSS architecture_: The 7-1 rule, component-based design, the BEM methodology, writing reusable, maintainable and scalable code;

- *Implementing Sass in real-world projects:* setting global variables, mixins, using nesting syntax, building components for reusability, architecting CSS and managing media queries;

- *Using the NPM ecosystem:* setting up a development process to compile Sass and automatic browser reload, and creating a build process to concatenate, prefix and compress CSS files;

- _Making a webpage fully responsive:_ layout types, flexible images, using media queries to test for different screen widths, pixel densities and touch capabilities;

- *Using Videos in HTML and CSS:* building a background video effect;

- _Apply_ CSS animations with @keyframes, animation and transition;

## Compile SASS

As a package manager I used NPM (Node Package manager)

### Installing Node JS

Go to the [nodejs.org](https://nodejs.org/en/). Find a right Node JS installer for your platform.
Once installed open Command Line and check if you installed it successfully

`node –v`

it will show what version you have.

### Installing dependencies

1. Now, let’s navigate to your project folder

   `cd <path> / { project folder }`

2. Then run:

   `npm init`

   It will provide you with a walkthrough to create a `package.json` file.

3. Once package.json is created you need to install `node-sass` to compile sass files. `--save-dev` will save it in `package.json` as a dependency.

   `npm install node-sass --save-dev`

4. If you want your browser to automatically reload once you make changes to the code. You need to install `live-server`

   `npm install live-server`

   If it asks for permission, run this:

   `sudo npm install live-server`

5. To concatenate multiple files install `concat` :

   `npm install concat --save-dev`

6. Next you need to install `autoprefixer` and `postcss-cli`, which is part of `autoprefixer`:

   `npm install autoprefixer --save-dev`
   `npm install postcss-cli --save-dev`

7. Install `npm-run-all`. A CLI tool to run multiple npm-scripts in parallel or sequential.

   `npm intall npm-run-all --save-dev`

### Compile SASS

Once all dependencies are installed. Let’s create scripts for ‘package.json’ file to compile SASS file, autoprefix, concatenate and concatenate CSS files.

```javascript
"scripts": {
"watch:sass": "node-sass sass/main.scss css/style.css -w",
"devserver": "live-server",
"start": "npm-run-all --parallel devserver watch:sass",
"compile:sass": "node-sass sass/main.scss css/style.comp.css",
"concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
"prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.concat.css -o css/style.prefix.css",
"compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
"build:css": "npm-run-all compile:sass concat:css prefix:css compress:css"
}
```

When developing, run:

`npm start`

Once your project is ready. You can run:

`npm run build:css`

It will produce compressed `css/style.css` with concatenated `css/icon-font.css` and added prefixes, which was compiled from `sass/main.scss` in the first place.
