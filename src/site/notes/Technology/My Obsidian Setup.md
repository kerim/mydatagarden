---
{"dg-publish":true,"permalink":"/technology/my-obsidian-setup/","updated":"2024-03-17T11:26:57.101+08:00"}
---

A list of extensions I use to make Obsidian work well as a long-form writing app.

## Long Form Writing

- [Commentator](https://github.com/Fevol/obsidian-criticmarkup)
    - Supports CriticMarkup syntax for tracking changes, as well as adding comments and viewing them in the sidebar
- [Longform](https://github.com/kevboh/longform)
    - Concatenate multiple documents, strip code, and export. (I only use this at the end, as I find it a bit restrictive when working on early drafts.)
- [Pandoc Reference List](https://github.com/mgmeyers/obsidian-pandoc-reference-list)
    - Format and list all in-text citations. Autocomplete from Zotero API.
- [Templater](https://github.com/SilentVoid13/Templater)
    - Create default templates. Haven't tried yet
- [Writing Goals](https://github.com/lynchjames/obsidian-writing-goals)
    - Similar to what Ulysses offers

## Task management

- [Tasks](https://github.com/obsidian-tasks-group/obsidian-tasks)
    - View all tasks in vault, grouped by file

## Styling and UX

- [iA Writer theme](https://github.com/mrowa44/obsidian-ia-writer)
    - some conflicts with the task checkbox styling so I had to add some custom CSS snippets, see below.
- [Focus Mode](https://github.com/ryanpcmcquen/obsidian-focus-mode)
    - Quickly toggle focus mode
- [MySnippits](https://github.com/chetachiezikeuzor/MySnippets-Plugin)
    - Add and manage css snippits. Currently using for snippet that formats task checkboxes.
- [Typewriter Mode](https://github.com/davisriedel/obsidian-typewriter-mode)
    - Keep text in center and fade other paragraphs
- [Workspace Plus](https://github.com/nothingislost/obsidian-workspaces-plus)
    - Maintain multiple obsidian workspaces
- [Zoom](https://github.com/vslinko/obsidian-zoom)
    - Zoom in on header like an outliner

## Export

- [Obsidian Markdown Export](https://github.com/bingryan/obsidian-markdown-export-plugin)
    - One click export file to the Blot drafts folder
- [Pandoc Plugin](https://github.com/OliverBalfour/obsidian-pandoc)
    - For exporting to word documents or PDF. Not tested yet.

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