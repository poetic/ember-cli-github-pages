# ember-cli-github-pages

If you need to throw up a quick example of your addon in action, this is the
addon for you!

This addon provides new command(s) to help manage a gh-pages branch for your
addon. It's an addon for addons.

## Installation & Setup

First you need to install ember-cli-github-pages:

ember-cli - 0.1.5 and up
```sh
ember install:addon ember-cli-github-pages
```

ember-cli - 0.1.4 and below
```sh
npm install --save-dev ember-cli-github-pages
ember generate ember-cli-github-pages
```

Then you need to make the sure gh-pages branch is created and the unnecessary
files are removed:

```sh
git checkout --orphan gh-pages && rm -rf `ls -a | grep -vE '.gitignore|.git|node_modules|bower_components|\.\/|\.\.\/'` && git add . && git commit -m "initial gh-pages commit"
```

## Usage

Once that's done, you can checkout the branch you want to create the gh-page
from(likely master) and run the command to build and commit it.

```sh
git checkout master
ember github-pages:commit --message "Initial gh-pages release"
```

You will still need to push the gh-pages branch up to github using git. Once you
do that you can access the repo at `http://username.github.io/repo-name`. It may
take a few minutes after pushing the code to show up. 

## Authors

- [Jake Craige](http://twitter.com/jakecraige)

[We are very thankful for our many contributers](https://github.com/poetic/ember-cli-github-pages/graphs/contributors)

## Legal

[Licensed under the MIT license](http://www.opensource.org/licenses/mit-license.php)
