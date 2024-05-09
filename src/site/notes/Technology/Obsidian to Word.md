---
{"dg-publish":true,"permalink":"/technology/obsidian-to-word/","updated":"2024-05-09T20:36:01.716+08:00"}
---

This page has instructions on how to insert citations in Obsidian that can then be exported to a Word file. The setup allows you to enter citations in Obsidian with Zotero and continue to edit those citations using the Zotero plugin in Word after export. 

For a list of other plugins I use in Obsidian, see [[Technology/My Obsidian Setup\|My Obsidian Setup]].
## A list of tools mentioned in this article

#### Apps
- [Obsidian](https://obsidian.md/)
- Microsoft Word (Part of [Office 365](https://www.microsoft.com/en-us/microsoft-365/microsoft-office))
- [Zotero](https://www.zotero.org/)
- [Pandoc](https://pandoc.org/)
	- This app doesn't have a normal user interface (GUI), but installing it will allow other apps to have access to its commands. 
#### Zotero Plugins
- [Better BibTex](https://retorque.re/zotero-better-bibtex/)
	- Allows you to create a continuously updated export of your Zotero reference library that is formatted in such a way that it can "speak" to Pandoc.
#### Obsidian Plugins
- [Pandoc Reference List](https://github.com/mgmeyers/obsidian-pandoc-reference-list)
    - Format and list all in-text citations. Autocomplete from Zotero API.
- [Enhancing Export](https://github.com/mokeyish/obsidian-enhancing-export) 
	- Allows you to export from Obsidian to Microsoft Word (and other formats) using Pandoc. Especially useful is the fact that you can add custom Pandoc commands that will run by default, so once you have set things up the first time it should be fairly automatic.
#### Word Plugins
- Zotero
	- This is bundled with Zotero and should be installed automatically when you first start Zotero. If not, here are [instructions for installing it manually](https://www.zotero.org/support/word_processor_plugin_manual_installation). 

## Setup

The following steps should only need to be done once. After everything is setup, you shouldn't need to worry about them again.

#### Choose a folder
The important thing to decide, before you start, is what folder you will be using. That is because this is the same folder you will use for all the steps in this process. And it is a folder you will be setting as the location for all your Obidian document outputs as well, whenever you export your document to a Word file. 

In my case the folder resides in: `~/Documents/betterbiblatex`. I probably could have picked a better name, but I don't want to change it now, in case I break something in my workflow!
#### Setting up a BibTeX file
Make sure Better BibTex is installed (see above). Now go into Zotero and chose `export library` from the `file` menu. Then, when you get a popup, choose the format "Better BibLaTeX" from the menu. (I suppose you could choose `Better BibTex` - I'm honestly not too sure of the difference.) Make sure to check the boxes for `background export` and `keep updated`. Then click OK. Now you will be asked where to save it. Select the folder you decided on in the first step.

#### Download the Lua Filter
Navigate to [this page]((or just click [here](https://retorque.re/zotero-better-bibtex/exporting/pandoc/#from-markdown-to-zotero-live-citations)). in the Better BibTeX documentation, and scroll down to the section titled "From Markdown to Zotero live citations." (The link should take you right there). Then look for the text "download the Pandoc filter" and right-click on it and choose "save as." Save it in the folder you chose in the first step. Mine is called `zotero.lua`.

This file is the magic sauce that will allow Pandoc to create "live" citations in Word that can be edited by the Zotero plugin. The page offers more instructions if you want to modify the lua script to do other things.

#### Add a "reference" document
You will also want to add one more document to the folder you've been using. This is a Word Document that will serve as a reference for Pandoc when it creates styles for your document. For instance, what should a top level header look like? A block quote? 

[Here](https://github.com/maehr/academic-pandoc-template/) is the document I'm using now, but I'm not happy with it. The problem is that you can't just edit the text to change the styles, you have to go in and change the styles as defined in the "Styles Pane," which is a bit of a pain. Hopefully I can find a better one or edit this myself and share that here.
### Configure Enhancing Export
This is an Obsidian plugin. In the settings, choose the folder you have been using in the two previous steps as your default export path. 

Then, where it says "choose template" select `Word (.docx)`, and below that, where it says "extra arguments" add something like the following:

```
--reference-doc=~/Documents/betterbiblatex/reference.docx --lua-filter=~/Documents/betterbiblatex/zotero.lua --metadata=zotero_library:"My Library" --metadata=zotero_sorted:true
```

You will need to make sure that the folder name is the same as the one you chose in the first step. Replace "betterbiblatex" with whatever you chose. And if your "reference" doc has a different name, fix that as well. Finally, whatever your Zotero library name is, fix that here as well.
## Entering citations in Obsidian
When using Obsidian you want to enter citations in the standard format expected from Pandoc. You can reference [this guide](https://github.com/evolve2k/obsidian-pandoc-academic-word-doc-guide?tab=readme-ov-file) to see what that should look like, but the basic format is pretty simple: `[@friedmanDefiningEthnographicFilm2020,29]`. There are three important elements here: (1) the brackets that frame the reference, (2) the "citekey" which is generated from Zotero and is unique to each article (it will start with a "@" symbol and then include the surname of the first article followed by a shortened version of the title, and then the publication date - without any spaces), and (3) the page number being cited (after a comma). If you aren't citing a specific page you can leave out the comma and the page number, and just use the citekey inside square brackets. 

With the Pandoc Reference List plugin, once you start typing the "@" symbol and author name, it will suggest autocomplete options from your library. But don't forget to add the square brackets yourself! 

Pandoc Reference List will also show a sidebar with the fully formatted references.

## Refresh
This step is very important. Assuming you set up the Enhancing Export plugin to open the file in Word after export, it won't look right. You'll see some code where the Zotero formatted citations should be. This is easily fixed. Just switch to the Zotero plugin menu and click the "refresh" button. Once you do so, everything should be looking as if you had been using Word to format your Zotero citations all along! 

(Another way to do it, besides hitting "refresh," is to open the "Document Preferences" and then click OK.)

## Tips and Tricks
That's it for now. There is a lot more you can do, but I haven't tried any of these things yet, so I'm not ready to document them:
- Add metadata to your Obsidian document to pre-fill the title, author, date, and other fields in the Word Reference document.
- Export directly to a formatted PDF document without first going through the step of exporting to Word.
- Create a table of contents. 

## Acknowledgements
- I would like to thank the following three people for their help, without whom I never would have figured all this out:
	- User parfitt.christine in the Zotero forums, where she gave [the instructions](https://forums.zotero.org/discussion/comment/407793/#Comment_407793) that got me started.
	- retorquere, the developer of Better BibTeX who gave some [useful advice](https://github.com/retorquere/zotero-better-bibtex/discussions/2873).
	- And user jptownley in the Obsidian forums who showed me how to use Enhancing Export and a reference document.
	- And user FeralFlora in the Obsidian forums for additional feedback and suggestions on how to deal with reference documents.
