# Template Whisperer

A browser-based tool that checks and fixes docxtemplater `.docx` templates. Because Word silently destroys your templates every time you save them once they're complex, and your implementation may not give you error logs (despite the library having error logging..)

## What

- Validates tag syntax (`{model.data.xyz}`, loops, conditionals, filters)
- Detects XML run splits (Word formatting breaking tags across runs)
- Detects merged tag runs (tags sharing runs with surrounding text)
- Fixes everything with one button click

## How

Drop a `.docx` file on the page. It tells you what's wrong. Click "Fix & Download" and it gives you one that works.

Everything runs client-side in your browser. No server, no uploads, no analytics, no cyber, no tracking. No one wants to deal with your template anyway

## Technical

You don't need these, but since you're reading my README, you're digging for something:

- Uses [PizZip](https://github.com/open-xml-templating/pizzip) to read/write `.docx` archives in the browser. Fork of JSZip.
- Parses `<w:t>` text nodes from Word XML and maps them back to XML positions
- The fix wraps isolated tag runs in `<w:bookmarkStart/>`...`<w:bookmarkEnd/>` pairs so Word stops merging them on save
- Yes, bookmarks. I tried everything.

## Live

[https://adrklu.github.io/template-whisperer/](https://adrklu.github.io/template-whisperer/)
