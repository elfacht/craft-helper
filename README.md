# Craft CMS Macros and Components
A collection of Craft CMS [macros](https://docs.craftcms.com/v3/changes-in-craft-3.html#twig-2) and components I frequently use on projects. Feel free to use, alter and extend. Suggestions are welcome.

## How to use macros

I usually set the macro include in a first level template like `_router.html` from where I delegated all my pages and set `macros`as a parameter on includes:

```twig
{# _router.html or another first level template #}
{% set macros = 'partials/_/_macros.html' %}
{% set notfound = '404' %}

{% include ['pages/' ~ entry.type.handle, notfound] with { macros: macros } %}
```

In the page template I just import the macros and inherit it to the components:

```twig
{# page.html #}
{% import macros as helper %}

{# Macro: macros/include.twig #}
{{helper.include('modules', 'hero', {
	image: entry.image.one() ?? null,
	macros: macros
})}}
```

The `_macros.html` or .twig:

```twig
{% macro myMacro(param) %}
{# Do something here #}
{% endmacro %}
```

## License

Itsa [MIT](LICENSE.md)!
