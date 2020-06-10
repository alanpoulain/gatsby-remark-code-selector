# gatsby-remark-code-selector

Transform equivalent code blocks in Gatsby markdown files into a selector.

Example in the [API Platform website](https://api-platform.com/docs/):

![Example in the API Platform website](https://github.com/alanpoulain/gatsby-remark-code-selector/blob/master/img/api-platform-example.gif?raw=true)

### Dependencies

- `gatsby-transformer-remark`
- `gatsby-remark-prismjs`

### Features

- Selecting a language in a selector select the language for all the selectors in the page as well, if the language is available for them.
- The chosen language is kept in the local storage: if the page is refreshed or if another page is loaded, the language will be selected for all the selectors.

## How to install

Add the plugin to your project:

```shell
npm install --save gatsby-remark-code-selector
```

Configure the plugin:

```javascript
// gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-transformer-remark`,
      options: {
        plugins: [
          // gatsby-remark-prismjs must go
          // before gatsby-remark-code-selector
          `gatsby-remark-prismjs`,
          `gatsby-remark-code-selector`,
        ],
      },
    },
  ],
};
```

Restart Gatsby.

## How to use

In your markdown files:

````markdown
[codeSelector]
```php
<?php
use ApiPlatform\Core\Annotation\ApiResource;

/**
 * @ApiResource(itemOperations={"get"})
 */
class Book
{
    //...
}
```

```yaml
App\Entity\Book:
    itemOperations:
        get: ~
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<resources xmlns="https://api-platform.com/schema/metadata"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="https://api-platform.com/schema/metadata
           https://api-platform.com/schema/metadata/metadata-2.0.xsd">
    <resource class="App\Entity\Book">
        <itemOperations>
            <itemOperation name="get" />
        </itemOperations>
    </resource>
</resources>
```
[/codeSelector]
````

The code selector is *not stylized by default*.
You can add your own CSS by using the following class names:
- `code-selector` for the whole selector
- `code-selector-toolbar` for the container of the select buttons
- `code-selector-select-php` for a particular button
- `code-selector-code-php` for a particular code block
