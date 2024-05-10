---
{"dg-publish":true,"permalink":"/technology/obsidian-to-word/","updated":"2024-05-10T08:01:41.482+08:00"}
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

## Setup (quick start version)

The following steps should only need to be done once. After everything is setup, you shouldn't need to worry about them again.

Note: I have a Mac laptop and so these instructions are specific for MacOS. If someone would like to provide additional notes for Windows users I'd be happy to add them.

This quick start version will get you up and running in minutes. I also have [[Technology/Customizing Obsidian to Word\|a more advanced guide]] (very much a work-in-progress) for those who want greater customization. For instance, it is possible to specify the specific styles you want to use in the Word document that gets output.
#### 1 Create a folder
You need to have a folder where you will export your files for conversion. Because of how this conversion works, you need to use the same folder every time. So create it now and give it an easy to remember name. I recommend a name that is all lower case and has no spaces. I use `obsidian2word`, and the path to the folder is: `/Users/[name of your user folder]/Documents/obsidian2word `. That is, its in the root level of my Documents folder on my Mac. 

Since each person's user folder is named differently, you will have to check yours. On the Mac, you can get the full path to the folder (important for later on), by control-clicking on the folder in the Finder and then holding down the `option` key. This will show an option to copy the full folder path to your clipboard. 
#### 2 Download the Lua Filter
Navigate to [this page](https://retorque.re/zotero-better-bibtex/exporting/pandoc/#from-markdown-to-zotero-live-citations) in the Better BibTeX documentation, and scroll down to the section titled "From Markdown to Zotero live citations." (The link should take you right there). Then look for the following text: "download the Pandoc filter". Right-click on it and choose "save as." Save it in the folder you chose in the first step. Mine is called `zotero.lua`.

This file is the magic sauce that will allow Pandoc to create "live" citations in Word that can be edited by the Zotero plugin. The page where you downloaded it offers more instructions if you want to modify the lua script to do other things.
#### 3 Configure Enhancing Export
Enhancing Export is an Obsidian plugin. (See above.)

In the plugin settings, choose the folder you have been using in the two previous steps as your default export path. 

Then, where it says "choose template" select `Word (.docx)`, and below that, where it says "extra arguments" add the following:

```
--lua-filter=/Users/[name of your user folder]/Documents/obsidian2word 
```

See my notes on getting the full path to your folder from step 1.
## Entering citations in Obsidian
When using Obsidian you want to enter citations in the standard format expected from Pandoc. You can reference [this guide](https://github.com/evolve2k/obsidian-pandoc-academic-word-doc-guide?tab=readme-ov-file) to see what that should look like, but the basic format is pretty simple: `[@friedmanDefiningEthnographicFilm2020,29]`. There are three important elements here: (1) the brackets that frame the reference, (2) the "citekey" which is generated from Zotero and is unique to each article (it will start with a "@" symbol and then include the surname of the first article followed by a shortened version of the title, and then the publication date - without any spaces), and (3) the page number being cited (after a comma). If you aren't citing a specific page you can leave out the comma and the page number, and just use the citekey inside square brackets. 

With the Pandoc Reference List plugin, once you start typing the "@" symbol and author name, it will suggest autocomplete options from your library. But don't forget to add the square brackets yourself! 

Pandoc Reference List will also show a sidebar with the fully formatted references.

## Export
To export, open up the Obsidian command pallet by using the keyboard shortcut (`command-p` on a Mac). Then type `export`. You will see the option for "Enhancing Export: Export to..." Select that. Make sure to choose `Word (.docx)`  as your export format. 

## Refresh
This step is very important. Assuming you set up the Enhancing Export plugin to open the file in Word after export, it won't look right. You'll see some code where the Zotero formatted citations should be. This is easily fixed. Just switch to the Zotero plugin menu and click the "refresh" button. Once you do so, everything should be looking as if you had been using Word to format your Zotero citations all along! 

(Another way to do it, besides hitting "refresh," is to open the "Document Preferences" and then click OK.)

## Tips and Tricks
That's it for now. There is a lot more you can do, but I haven't tried any of these things yet, so I'm not ready to document them:
- Add a reference document telling the script how to style your Word document. (This is already documented in my [[Technology/Customizing Obsidian to Word\|Customizing Obsidian to Word]] guide.)
- Add metadata to your Obsidian document to pre-fill the title, author, date, and other fields in the Word Reference document.
- Export directly to a formatted PDF document without first going through the step of exporting to Word.
- Create a table of contents. 

## Acknowledgements
- I would like to thank the following three people for their help, without whom I never would have figured all this out:
	- User parfitt.christine in the Zotero forums, where she gave [the instructions](https://forums.zotero.org/discussion/comment/407793/#Comment_407793) that got me started.
	- retorquere, the developer of Better BibTeX who gave some [useful advice](https://github.com/retorquere/zotero-better-bibtex/discussions/2873).
	- And user jptownley in the Obsidian forums who showed me how to use Enhancing Export and a reference document.
	- And user FeralFlora in the Obsidian forums for additional feedback and suggestions on how to deal with reference documents.
