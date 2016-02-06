# ember-cli-github-pages

[![Join the chat at https://gitter.im/poetic/ember-cli-github-pages](https://badges.gitter.im/poetic/ember-cli-github-pages.svg)](https://gitter.im/poetic/ember-cli-github-pages?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![npm version](https://badge.fury.io/js/ember-cli-github-pages.svg)](http://badge.fury.io/js/ember-cli-github-pages)
[![Ember Observer Score](http://emberobserver.com/badges/ember-cli-github-pages.svg)](http://emberobserver.com/addons/ember-cli-github-pages)
[![Code Climate](https://codeclimate.com/github/poetic/ember-cli-github-pages/badges/gpa.svg)](https://codeclimate.com/github/poetic/ember-cli-github-pages)  
[![Dependency Status](https://david-dm.org/poetic/ember-cli-github-pages.svg)](https://david-dm.org/poetic/ember-cli-github-pages)
[![devDependency Status](https://david-dm.org/poetic/ember-cli-github-pages/dev-status.svg)](https://david-dm.org/poetic/ember-cli-github-pages#info=devDependencies)


If you need to throw up a quick example of your addon in action, this is the
addon for you!

This addon provides new command(s) to help manage a gh-pages branch for your
addon. It's an addon for addons.

## Installation & Setup

First you need to install ember-cli-github-pages:

```sh
ember install ember-cli-github-pages
```

In order to have any assets you have in your repo load correctly you need to add the following to your `tests/dummy/config/environment.js` file:
```javascript
if (environment === 'production') {
  ENV.baseURL = '/name-of-your-repo'
}
```

Commit these changes `git add -A && git commit -m "Added ember-cli-github-pages addon"`

Then you need to create the gh-pages branch and remove the unnecessary files:

```sh
git checkout --orphan gh-pages && rm -rf `ls -a | grep -vE '\.gitignore|\.git|node_modules|bower_components|(^[.]{1,2}/?$)'` && git add -A && git commit -m "initial gh-pages commit"
```

## Usage

Once that's done, you can checkout the branch you want to create the gh-page
from(likely master) and run the command to build and commit it.

Then run ember github-pages:commit --message "some commit message" in order to rebuild gh-pages branch.

```sh
git checkout master
ember github-pages:commit --message "Initial gh-pages release"
```
### Ember Addons: Add a Demo URL

Once you've created a gh-pages branch, tell the world! Add a `demoURL` key to the `ember-addon` object in your `package.json`. See the `ember-cli` [documention](http://ember-cli.com/extending/#configuring-your-ember-addon-properties) for details.

### A note about Org and User Pages

While in general, github repo pages will serve the content in the `gh-pages` branch, [org and user pages](https://help.github.com/articles/user-organization-and-project-pages/#user--organization-pages) serve content in the `master` branch. When using this addon to develop a Org or User page, edit your Ember Application on an alternate branch such as `ember`. Once you are ready to build the application and send to GitHub you can either:

* add the `--branch master` option to the `ember github-pages:commit` command
* make the `gh-pages` branch on your local machine track the master branch on `origin` via the command:

```sh
git branch --set-upstream gh-pages origin/master
```

### Advanced Usage

You may optionally specify an ember build environment and a branch name as parameters

```sh
git checkout master
ember github-pages:commit --message "Initial demo app release" \
                          --branch="my-demo-app" \
                          --environment=development
```
| Optional Argument | Default Value | Description |
|-------------------|---------------|-------------|
| environment       | `production`  | Ember build environment (i.e., `development`, `production`) |
| branch            | `gh-pages`    | Branch to commit your app to |

You will still need to push the gh-pages branch up to github using git. Once you
do that you can access the repo at `http://username.github.io/repo-name`. It may
take a few minutes after pushing the code to show up. 

## Authors

- [Jake Craige](http://twitter.com/jakecraige)

[We are very thankful for our many contributors](https://github.com/poetic/ember-cli-github-pages/graphs/contributors)

## Legal

[Licensed under the MIT license](http://www.opensource.org/licenses/mit-license.php)
