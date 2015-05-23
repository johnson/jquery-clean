Takes dirty dirty (X)HTML and produces nice clean XHTML

It will;
  * fix self closing tags
  * lower-case tags
  * remove non-standard attributes
  * remove in-line style attributes
  * remove in-line event attributes
  * optionally remove other attributes
  * tidy unnecessary white space and new lines
  * remove comments
  * remove proprietary word formatting tags
  * replace tags e.g. i=>em
  * optionally leave css classes in place
  * format and indent html

### Options ###

| **Name** | **Description** | **Example Value** |
|:---------|:----------------|:------------------|
| bodyOnly | clean the body tag only | `true|false`      |
| allowedTags | only allow tags in this array, (white list), contents still rendered | `["p","em"]`      |
| removeTags | remove tags in this array, (black list), contents still rendered | `["strong"]`      |
| allowedAttributes | array of attributes to allow on all tags or those specified | `[["id"], ["style", ["p", "dl"]]]` |
| removeAttrs | array of attributes to remove on all tags | `[class]`         |
| allowedClasses | array of allowed classes | `["left","right"]` |
| format   | format html     | `true|false`      |
| formatIndent | indent starting point | `2`               |
| replace  | replace matching tags with another tag, match by string or regex | `[["b", "big"], "strong"]` |
| replaceStyles | styles to replace with elements | `[[/font-weight:\s*bold/i, "strong"], [/regex/, replacement]]` |
| allowComments | allow or remove comments, false by default | `true|false`      |
| allowEmpty | allow the tags in this array to be empty | `["p"]`           |

### Example ###

```
$.htmlClean("<H1 class=\"header\"><P>Nested P Test</H1>", {format:true});

=> 
<h1>
	Nested P Test
</h1>
```

Demo
http://www.antix.co.uk/Content/Demos/jQuery-htmlClean/Test.htm

jQuery Plug-in page
http://plugins.jquery.com/project/htmlClean

## 1.4.0 ##
added allowEmpty to options, allows empty tags mentioned
better formatting
other bug fixes

## 1.3.0 ##
added allowedAttributes option a list of the attributes allowed on a tag
in addition to the internal defaults
notRenderedTags removed functionality covered by removeTags

## 1.2.2 ##
replaceStyles added for replacement of bold, italic, super and sub styles on an element
this is to add more robust style/tag replacement

Multiple style matches supported, inline elements are replaced by the first match, block-level elements are retained

## 1.2.0 ##
Black and white lists added, see allowedTags and removeTags above
Thanks to thanks to David Wartian (Dwartian) for suggestion and code

## 1.1.0 ##
Now you can specify css classes that you want to retain
Also, it formats and indents the cleaned html, default is false

## 1.0.1 ##
Trim start fix

Whitespace on inline elements fixed

## 1.0.0 ##
Bug fixes for greedy attribute selection and order of attribute removal

Trim functions:
|$.htmlClean.trim()|Trims a string start and end|
|:-----------------|:---------------------------|
|$.htmlClean.trimStart()|Trims the start of a string |
|$.htmlClean.trimEnd()|Trims the end of a string   |
|$.htmlClean.trimStartIndex()|Gets the index of a trim start|
|$.htmlClean.trimEndIndex()|Gets the index of a trim end|

**nb These functions do not use regex to trim and are therefore safe to use in a regex.exec loop**

## 0.9.3 ##
Now cleans web kit span style tags
`<span class="Apple-style-span" style="font-weight: bold;">  =>  <strong>`

jQuery function added
` $("#SomeElement").htmlClean() `