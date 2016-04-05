# IYV

## Minimal Setup
1. Clone or fork this repository
1. `$ npm install` – install development dependencies
1. `$ npm run build` – build assets (CSS, e.g.)
1. `$ npm start` – start a development server so the paths to resources don't get jacked up
1. Navigate to `http://localhost:3000`

## Development
To start the development server, run
```
$ npm start
```
from the project folder and then navigate to `http://localhost:3000`

### HTML Development
Keep it simple! All HTML files and other assets should be located within the `public` folder.

### CSS Development
There is nothing fancy here except for a few Sass modules (files) being compiled and compressed into 1 `.css` file. The CLI (command-line interface) commands are located in executable files within `bin/` and are executed in `package.json` by NPM scripts.

To compile the Sass:
```
$ npm run build-css
```

To watch for changes to `src/styles/` and re-compile:
```
$ npm run watch-css
```

### Deploy to `gh-pages`
If you want this to be continually easy, create this script somewhere in your path (mine is `~/bin/git-gh-deploy`):
```sh
#!/bin/sh
if [ -z "$1" ]
then
  echo "Which folder do you want to deploy to GitHub Pages?"
  exit 1
fi
git subtree push --prefix $1 origin gh-pages
```
Next, from within this project folder and in the `master` branch, once you're ready to rock and roll, run
```
$ git-gh-deploy public
```
This should take everything from the `public` folder and place it over in the `gh-pages` branch.

If you find the `git-gh-deploy` command unavailable, add this line to your `~/.bash_profile`:
```
export PATH=/Users/youruserhere/bin:$PATH
```

## So, All Together!
Here's a basic flow for making your changes, pushing to the master
branch and deploying to GitHub Pages:
```
$ git pull origin master
$ git add -A
$ git commit -m "These are some changes that do X, Y and Z"
$ git push origin master
$ git-gh-deploy public
```
If you create a separate branch that is to be merged in to master via a Pull Request, then just make sure you pull the `master` branch and then do the `git-gh-deploy` line.
