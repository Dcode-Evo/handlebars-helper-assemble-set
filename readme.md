# Handlebars helper {{set}} for Assemble

Allows to set a variable diractly in the HTML

You can use JS to set a dynamic value, JS expression will be eval() if possible.
You can disable JS eval() by the parameter jsEnabled=false

- `{{set myVar = "This is a variable for <%= lang %>"}}` -> myVar = "This is a variable for fr"
- `{{set myVar = '{"key": "value", "key2": "value"}'}}` -> strict usage of single/double quotes '{"key" : "value"}'
- `{{set myVar = "1 + 1"}}` -> myVar = 2
- `{{set myVar = "1 + 1" jsEnabled=false }}` -> myVar = "1 + 1"
- `{{set myVar = "Math.random() * (10 - 1) + 1"}}` // => myVar will contain a number between 1 and 10

```handlebars 
{{set int = 1}}`
{{set calc='<%= int %> + 2'}}
```

`calc` value will be `3`: `<%= int %>` will be interpreted as `1` => `1 + 2 = 3`

_can contain assemble variables with the same syntax that in grunt config `<%= myVar %>`_

Useful with conditions:
```handlebars
{{#is lang 'fr'}}
    {{set show = true}}
{{else}}
    {{set show = false }}
{{/is}}

{{#if show}}
    <div>Visible in French mail</div>
{{/if}}

_________

Have fun.