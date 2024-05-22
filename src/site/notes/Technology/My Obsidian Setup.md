---
{"dg-publish":true,"permalink":"/technology/my-obsidian-setup/","updated":"2024-05-22T09:25:52.286+08:00"}
---

Some of of extensions I use to make Obsidian work well as a long-form writing app. See [[Technology/My digital toolkit\|My digital toolkit]] for an overview of how I use Obsidian for my work. 

## Working with Citations

I've created [[Technology/Obsidian to Word\|a separate page]] for instructions on how to insert citations in Obsidian that can then be exported to a Word file. The setup allows you to enter citations in Obsidian with Zotero and continue to edit those citations using the Zotero plugin in Word after export. As well as a page for more advanced [[Technology/Customizing Obsidian to Word\|customizations]] when exporting.

## Long Form Writing
- [Longform](https://github.com/kevboh/longform)
	- Provides a number of tools to help you to combine shorter notes into a longer manuscript, including saving drafts, setting writing goals, and processing for export to other apps.
- [Obsidian Footnote Shortcut](https://github.com/akaalias/obsidian-footnotes/tree/0.0.5)
	- These markdown formatted footnotes can be converted to regular footnotes using the same procedure described for exporting your document with citations. 
	- Not sure if it is necessary but the [Tidy Footnotes](https://github.com/charliecm/obsidian-tidy-footnotes) plugin will re-number your footnotes sequentially if they get out of order due to cut and paste. 
- [Focus Mode](https://github.com/ryanpcmcquen/obsidian-focus-mode)
    - Quickly toggle focus mode to hide distractions
- [Typewriter Mode](https://github.com/davisriedel/obsidian-typewriter-mode)
    - Keep text in center and fade other paragraphs

## Track Changes
- [Commentator](https://github.com/Fevol/obsidian-criticmarkup)
    - Supports CriticMarkup syntax, a markdown-based syntax for tracking changes, as well as adding comments and viewing them in the sidebar. Note that this is still in beta - you need to install it with the BRAT plugin below. I wouldn't recommend this unless you know what you are doing, but a neat trick is to ask ChatGPT to use CriticMarkup when making suggestions on your writing. That way you can go through the suggestions one-by-one and accept or reject them individually. 
- [BRAT](https://github.com/TfTHacker/obsidian42-brat)
    - Need this to easily install Commentator, which is in beta
## Styling and UX
- [iA Writer theme](https://github.com/mrowa44/obsidian-ia-writer)
    - some conflicts with the task checkbox styling so I had to add some custom CSS snippets, see below.
- [MySnippits](https://github.com/chetachiezikeuzor/MySnippets-Plugin)
    - Add and manage css snippits. Currently using for snippet that formats task checkboxes.
- [Recent Files](https://github.com/tgrosinger/recent-files-obsidian)
	- Adds a tab to show recent files

## Blog and Newsletter Related
I keep separate Obsidian vaults for different purposes. One for longform writing, one for my blog, one for my digital garden (this website), and one for my newsletter. This allows me to better customize each one for different workflows. Here are some I use for my blog and newsletter

- [Obsidian Markdown Export](https://github.com/bingryan/obsidian-markdown-export-plugin)
    - Use this for my blog, as it gives one-click export to my Blot folder.
- [Filename Heading Sync](https://github.com/dvcrn/obsidian-filename-heading-sync)
	- Makes the first heading match the file name. (I only use this one for my blog, otherwise it isn't needed.)
- [Send to Ghost](https://github.com/Southpaw1496/obsidian-send-to-ghost)
	- I use this for writing my newsletter, which is hosted on Ghost.

## Custom CSS sippets

Added this to the [alternative checkbox](https://github.com/netgamesekai/obsidian-checkbox-css) css because the iA Writer theme tries to force its own plain text checkboxes.

```
/* Custom styles for checkboxes */
body input[type="checkbox"].task-list-item-checkbox {
  /* Reset default checkbox appearance */
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  background: transparent;
  width: 15px; /* Custom width */
  height: 15px; /* Custom height */
  border: 2px solid var(--checkbox); /* Custom border */
  cursor: pointer; /* Hand cursor on hover */
  position: relative; /* To position pseudo-elements */
}

/* Override the ::after pseudo-element for unchecked tasks */
body input[type="checkbox"].task-list-item-checkbox:not(:checked)::after {
  content: none;
}

/* Custom styling for checked state */
body input[type="checkbox"].task-list-item-checkbox:checked {
  background-color: var(--checkbox-done); /* Example checked color */
  /* Add other styles for checked state if needed */
}

```

I also like high contrast orange text:

```
body, p {
  color: #f6ad55 !important; /* Bright orange color, with !important to ensure it overrides other styles */
}

```