# Detection Patterns

Regex patterns for finding common WCAG violations via static code analysis.

## Images

```
<img(?![^>]*alt=)
<svg(?![^>]*aria-label)(?![^>]*role="presentation")
<input\s[^>]*type="image"(?![^>]*alt=)
<object(?![^>]*aria-label)(?![^>]*title=)
```

## Forms

```
<input(?![^>]*aria-label)(?![^>]*id=.*<label[^>]*for=)
<select(?![^>]*aria-label)(?![^>]*id=)
```

## ARIA

```
role="(?!alert|alertdialog|button|checkbox|combobox|dialog|grid|gridcell|img|link|list|listbox|listitem|log|marquee|math|menu|menubar|menuitem|menuitemcheckbox|menuitemradio|navigation|none|note|option|presentation|progressbar|radio|radiogroup|region|row|rowgroup|rowheader|search|separator|slider|spinbutton|status|switch|tab|tablist|tabpanel|textbox|timer|toolbar|tooltip|tree|treegrid|treeitem)[a-z]+"
aria-hidden=["']true["'][^>]*tabindex=(?!["']-1)
aria-hidden=["']true["'][^>]*<button
aria-hidden=["']true["'][^>]*<a\s
```

## Structure

```
<html(?![^>]*lang=)
<title>\s*</title>
<title/>
```

## Headings

```
# Look for heading level skips by searching for headings and verifying sequence:
<h[1-6]
# Empty headings:
<h[1-6][^>]*>\s*</h[1-6]>
```

## Keyboard & Focus

```
tabindex=["'][1-9]
outline:\s*none
outline:\s*0[^.]
```

## Tables & Frames

```
<table(?![^>]*role=["']presentation)(?![\s\S]*?<th)
<th(?![^>]*scope=)
<th[^>]*>\s*</th>
<iframe(?![^>]*title=)
```

## Deprecated Elements

```
<blink
<marquee
<meta[^>]*http-equiv=["']refresh
autoplay(?![^>]*muted)
```

## Buttons & Links

```
<button[^>]*>\s*</button>
<a[^>]*>\s*</a>
<a[^>]*>click here</a>
<a[^>]*>here</a>
<a[^>]*>read more</a>
```

## Color (flags for manual review)

```
color:\s*#[a-fA-F0-9]{3,8}
background-color:\s*#[a-fA-F0-9]{3,8}
style=["'][^"']*color:
```
