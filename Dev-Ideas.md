## Rendering

```
document.pdf.md.eco
> pdf.render(md.render(eco.render(document)))
> document.pdf

document.pdf.html.md.eco
> pdf.render(html.render(md.render(eco.render(document))))
> document.pdf

document.pdf.html.md.eco
> pdfFromEco(htmlFromMd(mdFromEco(document)))
> document.pdf

document.md extends layout.html.eco
> html.render(eco.render(layout, md.render(document)))
> document.html

document.md
> md.render(document)
> document.md (as html)

document.md
> document.md (as md)

document.html.md
> htmlFromMd.render(document)
> document.html (as html)
```

``` coffeescript
markdownRenderer = class extends BaseRenderer
  supportedExtensionCombinations: [
    {in:/^md|markdown$/, out: /^html$/}
  ]
  render: (inExtension, outExtension, content) ->
    markdown.render content

ecoRenderer = class extends BaseRenderer
  supportedExtensionCombinations: [
    {in:/^.*$/, out: /^.*$/}
  ]
  render: (inExtension, outExtension, content) ->
    eco.render content
```