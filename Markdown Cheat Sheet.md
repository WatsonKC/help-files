Markdown Cheat Sheet
====================

Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax) and [extended syntax](https://www.markdownguide.org/extended-syntax).

# Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

## Headings
|Element|Syntax|Example|
|-------|------|-------|
|Heading 1|# H1|<h1>H1</h1>|
|Heading 2|## H2|<h2>H2</h2>|
|Heading 3|### H3|<h3>H3</h3>|

## Styled
|Element|Syntax|Example|
|-------|------|-------|
|Bold|\*\*bold text\*\*|**bold text**|
|Italic|\*italicized text\*|*italicized text*|
|Strike through|\~\~The world is flat.\~\~|~~The world is flat.~~|
|Block quote|> blockquote|<blockquote>blockquote</blockquote>|
|Code|\`code\`|`code`|
|Fenced Code|\`\`\`<br/>{<br/>&emsp;"firstName": "John",<br/>&emsp;"lastName": "Smith",<br/>&emsp;"age": 25<br/>}<br/>\`\`\`|<code><br/>{<br/>&emsp;"firstName": "John",<br/>&emsp;"lastName": "Smith",<br/>&emsp;"age": 25<br/>}<br/></code>|
|Horizontal rule|---|<hr>|
|Footnote|Here's a sentence with a footnote. [^1]<br/><br/>[^1]: This is the footnote.|Here's a sentence with a footnote. <a href="#foot-1">[1]</a><br/><br/><p id="foot-1">[1] This is the footnote.</p>|

## Lists
|Element|Syntax|Example|
|-------|------|-------|
|Ordered|1. First item<br/>2. Second item<br/>3. Third item|<ol><li>First item</li><li>Second item</li><li>Third item</li></ol>|
|Unordered|- First item<br/>- Second item</br>- third item|<ul><li>First item</li><li>Second item</li><li>Third item</li></ul>|
|Tasks|- [x] Write the press release<br/>- [ ] Update the website<br/>- [ ] Contact the media|<ul><li>[x] Write the press release</li><li>[ ] Update the website</li><li>[ ] Contact the media</li></ul>|

## Multimedia
|Element|Syntax|Example|
|-------|------|-------|
|Link|\[Markdown Guide\]\(https://www.markdownguide.org\)|[Markdown Guide](https://www.markdownguide.org)|
|Image|\!\[alt text\]\(https://www.markdownguide.org/assets/images/tux.png\)|![alt text](https://www.markdownguide.org/assets/images/tux.png)|