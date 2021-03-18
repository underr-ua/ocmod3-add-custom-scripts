# Document addTag

## Short description
The «Document addTag» extension is for OpenCart 3 CMS. It is a helper tool that extends standard OpenCart class "Document" by adding two methods - addTag and getTags to allow store and embed any html tags with custom attributes and content.

1. To add a tag use `$this->document->addTag($tag, $id, $group)`, where:
* $tag is an array with tag data - tag name, content and attributes or properties, for example:
```
array(
    'tag'     => 'a',
    'content' => 'Click!',
    'attrs'   => array('href' => 'https://example.com')
    'close'   => true
```
* $id is an unique id to identify this entry.
* $group is a group where the tag will be placed (e.g, 'header' or 'footer')

2.To get tags use something like the next:
```
$tags = ''.

if ($this->document->getTags('header')) {
    foreach ($this->document->getTags('header') as $tag) {
        if ($tag['id'] == $route) {
            $tags .= '<' . $tag['tag']['name'];

            $attrs = '';

            foreach ($tag['tag']['attrs'] as $attr => $value) {
                $attrs .= $attr . '="' . $value . '" ';
            }

            $tags .= ' ' . $attrs;

            if (isset($tag['tag']['close']) && $tag['tag']['close']) {
                $tags .= '>';
            } else {
                $tags .= ' />';
            }

            $tags .= $tag['tag']['content'];

            if (isset($tag['tag']['close']) && $tag['tag']['close']) {
                $tags .= '</' . $tag['tag']['name'] . '>';
            }
        }
    }
}
```

## License
Licensed under the [MIT License](https://git.io/JqJxe)

