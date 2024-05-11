---
{"dg-publish":true,"permalink":"/technology/customizing-obsidian-to-word/","updated":"2024-05-11T07:57:37.030+08:00"}
---

This is a supplement to my [[Technology/Obsidian to Word\|Obsidian to Word]] guide, showing some additional options you can add to customize how Obsidian exports documents to Microsoft Word. It is a work-in-progress.

#### Add a "reference" document
You can add an additional document to export folder described in the quick setup workflow. This is a Word Document that will serve as a reference for Pandoc when it creates styles for your document. For instance, what should a top level header look like? A block quote? 

My own document can be found [here](https://github.com/kerim/pandoc-setup). And you can find something closer to the default document used by Pandoc [here](https://github.com/maehr/academic-pandoc-template/) .z

If you want to edit these, note that you can't just edit the text to change the styles, you have to go in and change the styles as defined in the "Styles Pane." For instance, click on the text that says "Header 1" and then you will see the "Header 1" style selected in the styles pane. Click on that and select "modify style" from the menu. Do not just use the default Word formatting choices to change the style in the document itself, as that won't modify the underlying style.

If you do this, you also need to let the "Enhancing Export" plugin know about it in the settings, but adding this line to your instructions that go in the "extra arguments"field.

```
--reference-doc=/Users/[name of your user folder]/Documents/obsidian2word/reference.docx
```

#### Document data for export
When exporting to Pandoc you can pre-set some data that will automatically filled in for you. This works together with the reference document discussed above. For instance, you can specify the document title, subtitle, author, date, etc. and then it will fill out the fields with those names as laid out in the reference document. 

Doing this is easy, just add something like this at the top of your document. Make sure to include the three dashes before and after the text.

```

---
title: My cute article title
subtitle: Longer text which says what the article is actually about
author: My Name
​date: May 11, 2024

---

```

#### Merging multiple documents
The workflow I've described in these pages works with the "Enhancing Export" plugin, which does not currently support embedding files. That means you can't merge multiple files at the time of export. My current workaround is to use the ["Easy Bake" plugin](https://github.com/mgmeyers/obsidian-easy-bake) for Obsidian. That is, first you merge the documents and then you export to Word with "Enhancing Export." 