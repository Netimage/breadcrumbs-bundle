Breadcrumbs
===========

A magic way to create breadcrumbs for symfony applications.

**features**
* build breadcrumbs through current request uri.

[![Build Status](https://travis-ci.org/yceruto/breadcrumbs-bundle.svg?branch=master)](https://travis-ci.org/yceruto/breadcrumbs-bundle)

Installation
------------

### Step 1: Download the Bundle

```bash
$ composer require yceruto/breadcrumbs-bundle
```

This command requires you to have Composer installed globally, as explained
in the [Composer documentation](https://getcomposer.org/doc/00-intro.md).

### Step 2: Enable the Bundle

```php
<?php
// app/AppKernel.php

// ...
class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Yceruto\Bundle\BreadcrumbsBundle\BreadcrumbsBundle(),
        );
    }

    // ...
}
```

Usage
-----

### Render the breadcrumbs into any twig template

```twig
{{ render_breadcrumbs() }}
```

### Customize the breadcrumbs template

By default the breadcrumbs is rendered through `@Breadcrumbs/breadcrumbs/breadcrumbs.html.twig` template. You can to create a custom template 
named `breadcrumbs.html.twig` within `app/Resources/views/breadcrumbs/` directory in your project structure.

```twig
{# app/Resources/views/breadcrumbs/breadcrumbs.html.twig #}

<ol class="breadcrumb">
    {% for node in breadcrumbs %}
        {% set label = 'breadcrumbs.' ~ node.name %}
        {% if not loop.last %}
            <li><a href="{{ node.path }}"><i class="fa fa-home"></i> {{ label|trans }}</a></li>
        {% else %}
            <li class="active">{{ label|trans }}</li>
        {% endif %}
    {% endfor %}
</ol>
```

Resources
---------

You can run the unit tests with the following command:

    $ cd path/to/breadcrumbs-bundle/
    $ composer install
    $ phpunit

License
-------

This software is published under the [MIT License](LICENSE)
