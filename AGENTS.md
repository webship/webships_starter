# Webships Starter — agent guide

A `drupal-recipe` site template (`drupal/webships_starter`), the default one of
the Webships installer: a web apps gallery served through a documented API. Part
of the Webship Workspace (`~/workspace/products`): DDEV only.

## Rules

- This is a `drupal-recipe`: keep configuration in the recipe, not in
  `config/install` or `config/optional`.
- A site template is standalone. It never requires or applies another site
  template; shared parts come from module recipes.
- Only packages from drupal.org. The Swagger UI asset library belongs to the
  project template, where `installer-paths` works.
- JSON:API stays read-only. Never set `read_only: false` here.
- The Drupal core administration theme is the default theme, for the back end
  and the front end.

## Still to move here

The apps and organizations content model (the `webapp` and `organization`
content types, their fields and displays, the gallery views and the taxonomy
vocabularies) still lives in the `config/install` of the Webships profile. It
belongs in this recipe, so the profile can become an installer that only lists
site templates and then uninstalls itself.

## Build and test with DDEV

```bash
ddev composer require drupal/something
ddev drush cr
```

`ddev start` takes `-y`; `ddev stop` does not.

## Test

```shell
ddev drush site:install ../recipes/webships_starter -y
ddev drush config:get jsonapi.settings read_only
ddev drush config:get system.theme
```
