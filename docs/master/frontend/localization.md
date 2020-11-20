# Localization
Zest's localization features provide a convenient way to retrieve strings in various languages, allowing you to easily support multiple languages within your application. Language strings are stored in files within the `App/Locale` directory and for components it locate `/Component_Name/Locale.

## printl function

printl function is use to get language string value form language string file (this function isn't work in components)

```php
  echo printl('home:welcome');

```

## printc function

printc function is use to get language string value form language string file only in components

```php
  echo printc('home:welcome');

```

!!! info
    the language file is locate in Local folder


#### Zest

`App/Local`

#### Components

`App/Components/{name}/Local`  `{name}`  refer to component name
