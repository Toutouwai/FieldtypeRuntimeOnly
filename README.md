# Fieldtype Runtime Only

Not a proper fieldtype because it doesn't save data to the database. The fieldtype only exists to provide a convenient way to add an inputfield to templates that will render some markup at runtime.

For a field named "my_field"...

* Inputfield markup will be rendered from a file at `/site/templates/RuntimeOnly/my_field.php`. In addition to the standard ProcessWire variables this file receives:
    * `$page` - the page being edited.
    * `$field` - the Field object.
    * `$inputfield` - the Inputfield object.
* JS file `/site/templates/RuntimeOnly/my_field.js` will be added to admin if that file exists.
* CSS file `/site/templates/RuntimeOnly/my_field.css` will be added to admin if that file exists.

## Tips

### Output formatting

Output formatting for `$page` will be off in the context of Edit Page so if you want to use the formatted value of a field in your RuntimeOnly code you should use [$page->getFormatted()](https://processwire.com/api/ref/page/get-formatted/). E.g.
```php
$value = $page->getFormatted('some_field_name');
```

### Repeaters

If the RuntimeOnly field is used inside a Repeater field then you can get the Repeater page it is on via `$inputfield->hasPage`. E.g.
```php
$repeater_page = $inputfield->hasPage;
// Use $repeater_page as needed
echo "The name of the repeater page is $repeater_page->name";
```
