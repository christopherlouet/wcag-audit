# WCAG Audit Code Examples

Good and bad patterns for each audit category.

## 1. Images & Media

```tsx
// GOOD - Descriptive alt text
<img src="chart.png" alt="Sales growth chart showing 25% increase in Q4" />

// GOOD - Decorative image
<img src="decoration.png" alt="" role="presentation" />

// GOOD - Accessible SVG
<svg role="img" aria-label="Company logo">
  <title>Company logo</title>
  <path d="..." />
</svg>

// BAD
<img src="chart.png" />
<img src="chart.png" alt="image" />
<svg><path d="..." /></svg>
```

## 2. Forms

```tsx
// GOOD - Explicit label
<label htmlFor="email">Email address</label>
<input id="email" type="email" aria-describedby="email-hint" />
<span id="email-hint">We will never share your email</span>

// GOOD - Accessible error
<input id="email" type="email" aria-invalid={hasError} aria-describedby={hasError ? "email-error" : undefined} />
{hasError && (
  <span id="email-error" role="alert">Please enter a valid email</span>
)}

// BAD - No label
<input type="email" placeholder="Email" />
```

## 3. Keyboard Navigation

```tsx
// GOOD - Skip to content link
<a href="#main-content" className="sr-only focus:not-sr-only">
  Skip to main content
</a>
<main id="main-content">{/* content */}</main>

// GOOD - Focusable scrollable region
<div role="region" aria-label="Source code" tabIndex={0} style={{ overflow: 'auto' }}>
  <pre><code>{code}</code></pre>
</div>

// BAD - Positive tabindex
<button tabIndex={2}>Second</button>
<button tabIndex={1}>First</button>
```

```css
/* GOOD - Focus visible */
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

/* BAD - Focus removed */
:focus { outline: none; }
```

## 4. Buttons & Links

```tsx
// GOOD - Icon button with label
<button onClick={handleClose} aria-label="Close modal">
  <CloseIcon aria-hidden="true" />
</button>

// GOOD - External link
<a href="https://external.com" target="_blank" rel="noopener noreferrer">
  External docs
  <span className="sr-only">(opens in new tab)</span>
</a>

// BAD
<button onClick={handleClose}><CloseIcon /></button>
<a href="/pricing">Click here</a>
```

## 5. Color & Contrast

```tsx
// GOOD - Color + icon + text
<span className="error">
  <ErrorIcon /> This field is required
</span>

// BAD - Color only
<span style={{ color: 'red' }}>Error</span>
```

## 6. ARIA

```tsx
// GOOD - Valid ARIA usage
<div role="tablist" aria-label="Settings tabs">
  <button role="tab" aria-selected={true} aria-controls="panel-1">General</button>
  <button role="tab" aria-selected={false} aria-controls="panel-2">Security</button>
</div>
<div role="tabpanel" id="panel-1" aria-labelledby="tab-1">{/* content */}</div>

// GOOD - Listbox with correct children
<ul role="listbox" aria-label="Choose a color">
  <li role="option" aria-selected={true}>Red</li>
  <li role="option" aria-selected={false}>Blue</li>
</ul>

// BAD - Invented role
<div role="card">...</div>

// BAD - aria-hidden on focusable
<div aria-hidden="true">
  <button>This button is invisible but focusable!</button>
</div>

// GOOD - Accessible modal dialog
<dialog
  role="dialog"
  aria-modal="true"
  aria-labelledby="modal-title"
  aria-describedby="modal-desc"
>
  <h2 id="modal-title">Confirm deletion</h2>
  <p id="modal-desc">This action cannot be undone.</p>
  <button onClick={onConfirm}>Confirm</button>
  <button onClick={onCancel} autoFocus>Cancel</button>
</dialog>

// BAD - Modal without ARIA attributes or focus management
<div className="modal">
  <h2>Confirm</h2>
  <button onClick={onConfirm}>OK</button>
</div>
```

## 7. Structure & Semantics

```tsx
// GOOD - HTML with lang and descriptive title
<html lang="en">
  <head><title>Dashboard - MyApp</title></head>
</html>

// BAD - Missing lang, empty title
<html>
  <head><title></title></head>
</html>

// GOOD - Landmarks with unique labels
<header>
  <nav aria-label="Main navigation">{/* ... */}</nav>
</header>
<main><h1>Main content</h1>{/* ... */}</main>
<nav aria-label="Breadcrumb">{/* ... */}</nav>
<footer>{/* ... */}</footer>

// GOOD - Proper heading hierarchy
<h1>Main title</h1>
<h2>Section</h2>
<h3>Subsection</h3>

// BAD - Heading skip
<h1>Title</h1>
<h3>Subsection</h3>  {/* h2 missing */}
```

## 8. Tables

```tsx
// GOOD - Accessible data table
<table>
  <caption>Sales by quarter</caption>
  <thead>
    <tr>
      <th scope="col">Quarter</th>
      <th scope="col">Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Q1 2025</th>
      <td>$150,000</td>
    </tr>
  </tbody>
</table>

// BAD - Table without headers
<table>
  <tr><td>Q1</td><td>150,000</td></tr>
</table>
```

## 9. Frames & Iframes

```tsx
// GOOD
<iframe src="https://maps.example.com" title="Office location map" />

// BAD
<iframe src="https://maps.example.com" />
```

## 10. Deprecated Elements

```tsx
// BAD
<blink>Blinking text</blink>
<marquee>Scrolling text</marquee>
<meta httpEquiv="refresh" content="5;url=https://example.com" />
<video autoPlay src="video.mp4" />

// OK - Muted autoplay
<video autoPlay muted src="background.mp4" />
```

## 11. WCAG 2.2 - Target Size & Focus

```css
/* GOOD - Sufficient touch targets */
button, a, input, select {
  min-width: 44px;
  min-height: 44px;
}

/* GOOD - Focus not obscured by sticky elements */
.sticky-header { z-index: 100; }
:focus-visible { z-index: 101; position: relative; }
```

## Screen Reader Utility Class

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```
