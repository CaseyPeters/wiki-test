.. title:: Style Guides

Style Guides
============

The following are to coding standards that are followed for each programming languages. These are
considered best practices but are subject to change at any given point.

Magento
-------

For Magento projects it's recommended to follow `Magento Best Practices`_ by Ryan Street, some key
points include:

- **Never** edit core files.
- Split functionality into smaller modules.
- Make setup scripts for attributes required by the theme instead of creating them from the backend.
- Prefer event observers over class rewrites.
- Only make layout changes in the theme ``local.xml``.
- Keep PHP, CSS and Javascript code separate as much as possible.
- Keep ``.phtml`` files lean, move complex logic to a ``Block`` or ``Helper`` class.

.. _Magento Best Practices: http://www.coolryan.com/magento-best-practices/

PHP
---

Magento 1.X follows the `Zend Framwork Coding Standards`_ and Magento 2 follows `PSR-2`_ so the same
are followed when working on projects depending on each platform.

Some common conventions are:

- Indent code using 4 spaces instead of tabs.
- No trailing whitespace.
- Not more than 1 statement per line.
- The max line lenght should be 80 characters, ideally no more than 120 characters.
- Omit closing ``?>`` tag from files containing only PHP.

.. _Zend Framwork Coding Standards: http://framework.zend.com/manual/1.12/en/coding-standard.overview.html
.. _PSR-2: http://www.php-fig.org/psr/psr-2/

CSS / SCSS
----------

For CSS / SCSS files a slightly modified version of `Airbnb's CSS Style Guide`_ is followed.
The only difference is that 4 spaces are used for indentation instead of 2, the rest of the
rules include:

- Prefer dashes over camelCasing in class names.
- Do not use ID selectors.
- When using multiple selectors in a rule declaration, give each selector its own line.
- Put a space before the opening brace ``{`` in rule declarations.
- Put blank lines between rule declarations.
- Use ``.js-`` classes for Javascript hooks.

.. _Airbnb's CSS Style Guide: https://github.com/airbnb/css

Javascript
----------

For Javascript files a slightly modified version of `Airbnb's JS Style Guide`_ is followed.
The only difference is that 4 spaces are used for indentation instead of 2, the rest of the
rules include:

- Use the literal syntax for object creation.
- Use the literal syntax for array creation.
- Use single quotes ``''`` for strings.
- Use dot notation when accessing properties.
- Use one var declaration per variable.

.. _Airbnb's JS Style Guide: https://github.com/airbnb/javascript/tree/master/es5
