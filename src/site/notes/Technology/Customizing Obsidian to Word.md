---
{"dg-publish":true,"permalink":"/technology/customizing-obsidian-to-word/","updated":"2024-05-10T07:42:54.241+08:00"}
---

This is a supplement to my [[Technology/Obsidian to Word\|Obsidian to Word]] guide, showing some additional options you can add to customize how Obsidian exports documents to Microsoft Word. It is a work-in-progress.

#### Add a "reference" document
You can add an additional document to export folder described in the quick setup workflow. This is a Word Document that will serve as a reference for Pandoc when it creates styles for your document. For instance, what should a top level header look like? A block quote? 

[Here](https://github.com/maehr/academic-pandoc-template/) is the document I'm using now, but I'm not happy with it. The problem is that you can't just edit the text to change the styles, you have to go in and change the styles as defined in the "Styles Pane," which is a bit of a pain. Hopefully I can find a better one or edit this myself and share that here.

If you do this, you also need to let the "Enhancing Export" plugin know about it in the settings, but adding this line to your instructions that go in the "extra arguments"field.

```
--reference-doc=/Users/[name of your user folder]/Documents/obsidian2word/reference.docx
```
