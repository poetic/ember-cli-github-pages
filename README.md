# Ember-cli-github-pages

This addon provides new command(s) to help manage a gh-pages branch for your
addon. It's an addon for addons!

## Usage

First you need to install ember-cli-github-pages

```
npm install --save-dev ember-cli-github-pages
```

Then you need to make the sure gh-pages branch is created and the default files
are removed

```
git checkout -b gh-pages
rm -r `ls -a | grep -vE '.gitignore|.git'`
```
