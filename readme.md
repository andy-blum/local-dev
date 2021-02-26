# LocalDev Starter Kit

## What is this?

This is an opinionated starter kit for doing composer-based Drupal development
with DDEV & VS Code. Main points:

- **ProjectName.code-workspace**

  This is the settings for VS Code, featuring a multi-root workspace setup, some setting overrides, an xDebug listener, and a handful of recommended extensions

- **.ddev/config.yaml**

  Default settings from DDEV, with pre-start, post-start, and post-db-import hooks

- **composer.json**

  Default drupal/recommended-project composer template with additions

  - Added packages
    - `cweagans/composer-patches` to allow patch-handling in composer. Also added relevant composer config.
    - `drush/drush:^10`

  - Prevent Drupal scaffold from overwriting development.services.yml

  To apply patches to your project, add objects to the `patches` section of
  composer.json

  ```
  "patches": {
    "drupal/core": {
      "#issueid: Issue Title": "https://drupal.org/link/to/patch.patch",
      "#xxxxx: Other Issue Title": "https://drupal.org/link/to/otherpatch.patch"
    },
    "drupal/package_name": {
      "#yyyyyy: Module Issue Title": "https://drupal.org/link/to/mod_patch.patch"
    }
  }
  ```

- **/web/sites/development.services.yml**

  Add `twig.config` settings for local development. For this file to be useful,
  you'll need to create `settings.local.php` from `default.settings.php`.

## How do I use it?

This pro project is **not** intended to be something you should clone/fork and
start working on drupal from. This is intended to be a reference source to set
up your own local development environment and copy/paste useful parts from

0) Have Composer, DDEV, VS Code installed
1) Start a new Drupal project using the [recommended-project template](https://www.drupal.org/docs/develop/using-composer/starting-a-site-using-drupal-composer-project-templates#s-drupalrecommended-project)

  - D9: `composer create-project drupal/recommended-project my-project`
  - D8: `composer create-project drupal/recommended-project:^8.0 my-project`

2) `cd` into your new project's directory and run `ddev config`. Follow the
prompts.

3) Copy `ProjectName.code-workspace` to your project root and rename however
you like. Double-click the file and once the workspace loads, customize your
folder paths, settings, and recommended extensions as needed.

## You should/shouldn't do this, that, or the other thing.

I'm open to PRs, or fork this repo and customize your settings/extensions/etc.
