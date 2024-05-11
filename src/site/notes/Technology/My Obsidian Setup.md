---
{"dg-publish":true,"permalink":"/technology/my-obsidian-setup/","updated":"2024-05-11T19:41:57.178+08:00"}
---

A list of extensions I use to make Obsidian work well as a long-form writing app. See [[Technology/My digital toolkit\|My digital toolkit]] for an overview of how I use Obsidian for my work. 

## Working with Citations

I've created [[Technology/Obsidian to Word\|a separate page]] for instructions on how to insert citations in Obsidian that can then be exported to a Word file. The setup allows you to enter citations in Obsidian with Zotero and continue to edit those citations using the Zotero plugin in Word after export. As well as a page for more advanced [[Technology/Customizing Obsidian to Word\|customizations]] when exporting.

## Long Form Writing

- [Commentator](https://github.com/Fevol/obsidian-criticmarkup)
    - Supports CriticMarkup syntax for tracking changes, as well as adding comments and viewing them in the sidebar
- [Continuous Mode](https://github.com/gasparschott/obsidian-continuous-mode)
	- An Obsidian plugin that displays all open notes in a tab group as if they were a single continuous document (sometimes called "Scrivenings mode").
- [Obsidian Footnote Shortcut](https://github.com/akaalias/obsidian-footnotes/tree/0.0.5)
	- Not sure this is useful for academic writing? But it is great for writing blog posts if you want markdown styled footnotes in your post.

## Productivity

- [Tasks](https://github.com/obsidian-tasks-group/obsidian-tasks)
    - View all tasks in vault, grouped by file
- [Toggl Track](https://github.com/mcndt/obsidian-toggl-integration)
	- Can keep track of how much time you spend writing
- [Writing Goals](https://github.com/lynchjames/obsidian-writing-goals)
    - Similar to what Ulysses offers. Useful if you want to reach a particular word count each day.
- [Focus Mode](https://github.com/ryanpcmcquen/obsidian-focus-mode)
    - Quickly toggle focus mode to hide distractions
- [Typewriter Mode](https://github.com/davisriedel/obsidian-typewriter-mode)
    - Keep text in center and fade other paragraphs
## Styling and UX

- [iA Writer theme](https://github.com/mrowa44/obsidian-ia-writer)
    - some conflicts with the task checkbox styling so I had to add some custom CSS snippets, see below.
- [MySnippits](https://github.com/chetachiezikeuzor/MySnippets-Plugin)
    - Add and manage css snippits. Currently using for snippet that formats task checkboxes.
- [Workspace Plus](https://github.com/nothingislost/obsidian-workspaces-plus)
    - Maintain multiple obsidian workspaces. Another one I haven't actually used yet.
- [Zoom](https://github.com/vslinko/obsidian-zoom)
    - Zoom in on header like an outliner
- [Filename Heading Sync](https://github.com/dvcrn/obsidian-filename-heading-sync)
	- Makes the first heading match the file name. Can be useful for finding things later on if you change the title of the document.
- [Folder Focus Mode](https://github.com/grochowski/obsidian-folder-focus-mode)
	- Different from "Focus Mode" above, this is for your file list, and zooms in on the current folder.
- [Home tab](https://github.com/olrenso/obsidian-home-tab)
	- Gives you a start page, a bit like a web browser.
- [Recent Files](https://github.com/tgrosinger/recent-files-obsidian)
	- Adds a tab to show recent files
- [Tree Focus](https://github.com/iOSonntag/obsidian-plugin-treefocus)
	- Adds some formatting to highlight or dim items in your file tree

## Export

- [Obsidian Markdown Export](https://github.com/bingryan/obsidian-markdown-export-plugin)
    - One click export file to the Blot drafts folder
- [Send to Ghost](https://github.com/Southpaw1496/obsidian-send-to-ghost)
	- I use this for writing my newsletter, which is hosted on Ghost.

## Misc.

- [BRAT](https://github.com/TfTHacker/obsidian42-brat)
    - To install Commentator, which is in beta

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