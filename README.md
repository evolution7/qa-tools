# Evolution 7 QA Tools

This is a single repository for including all QA tools through Composer. If you install this as a `require-dev` requirement, you will have access to it on development and CI machines but don't need to install all the dependencies when deploying to your production environment.

## Installation

As stated above, the preferred way is to install it in your require-dev using

```bash
composer require --dev "evolution7/qa-tools=1.*"
```

## Included QA tools

* [PHPUnit](http://phpunit.de/)
* [phpDocumentor](http://www.phpdoc.org/)
* [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
* [PHPMD](http://phpmd.org/)
* [PHPCD](https://github.com/sebastianbergmann/phpcpd)
* [PHPLOC](https://github.com/sebastianbergmann/phploc)
* [PHP Depend](http://pdepend.org/)
* [PHP_CodeBrowser](https://github.com/Mayflower/PHP_CodeBrowser)

## CI examples

In the ci-examples directory you will find usage examples for these tools in a Continuous Integration setup.

## Git hooks

Included in this repository is also a collection of git hooks for use with the [git-hooks tool](https://github.com/icefox/git-hooks). This tool allows you to easily share git hooks in projects, and organize them cleanly.

### Usage

The easiest way to include these hooks is by first installing the [git-hooks tool](https://github.com/icefox/git-hooks) as discussed on its project page. To use the hooks in this repository you can then create a symlink from your project root `ln -s vendor/evolution7/qa-tools/git_hooks`, or create your own directory and copy/symlink only the hooks you wish to use.

### Hooks
The following hooks are present:

* post-merge/01-update-dependencies     - Runs a git composer install command and git submodule update after a pull.
* post-merge/11-grunt-build     - Updates npm/bower and runs grunt build after a pull. This checks if a Gruntfile actually exists before doing so.
* post-merge/21-build-symfony-model     - Symfony1.x build classes after a pull.
* post-merge/91-clear-cache     - Symfony1 clear cache after a pull.
* pre-commit/00-protect-master-staging  - Prevent commits to master and staging branches.
* pre-commit/01-composer    - Runs a git composer validate command before a commit.
* pre-commit/11-phplint    - Runs a lint check before commit.

# Contribute?

Feel free to fork this repository for your own customisations, or to create pull requests for including your preferred QA tool, Git Hook, or even CI example.
