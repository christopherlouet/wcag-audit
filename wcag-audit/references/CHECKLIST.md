# Manual Review Checklist (Needs Review)

Items that cannot be fully verified by static code analysis and require manual inspection.

## Images & Media

- [ ] Alt text is meaningful and describes the image content (not just "image" or filename)
- [ ] Decorative images are correctly identified (not all images with `alt=""` are truly decorative)
- [ ] Complex images (charts, infographics) have a long description or data table equivalent
- [ ] Audio descriptions are provided for video content when needed
- [ ] Captions are accurate and synchronized with video

## Forms

- [ ] Error messages clearly describe what went wrong and how to fix it
- [ ] Form instructions are clear before the user interacts
- [ ] Required fields are indicated in a way that doesn't rely on color alone
- [ ] Form can be completed and submitted using only keyboard

## Keyboard Navigation

- [ ] Focus order follows a logical reading sequence
- [ ] No content is only reachable via mouse hover
- [ ] Custom keyboard shortcuts don't conflict with screen reader shortcuts
- [ ] Modal dialogs trap focus correctly and return focus on close
- [ ] Dynamic content updates are announced to screen readers (live regions)

## Color & Contrast

- [ ] Text over images or gradients meets contrast ratios
- [ ] Contrast is maintained in dark mode / high contrast mode
- [ ] Interactive element states (hover, active, disabled) meet contrast requirements
- [ ] Data visualizations have non-color distinguishing features (patterns, labels)
- [ ] Links within text are distinguishable without relying on color alone

## ARIA & Semantics

- [ ] Custom components behave as expected with screen readers
- [ ] ARIA live regions announce dynamic content changes appropriately
- [ ] `aria-label` values are concise and meaningful
- [ ] Page content makes sense when read in DOM order (screen reader order)
- [ ] Language changes within content are marked with `lang` attribute

## Structure

- [ ] Page title accurately describes the page content
- [ ] Heading hierarchy conveys the document structure meaningfully
- [ ] Landmark regions cover all page content
- [ ] Navigation is consistent across pages

## Interactive Components

- [ ] Carousels/sliders can be paused and navigated via keyboard
- [ ] Tooltips are accessible via keyboard and persist long enough to read
- [ ] Autocomplete/dropdown suggestions are announced and navigable
- [ ] Drag-and-drop has a keyboard alternative
- [ ] Timeouts provide warnings and allow extension

## Touch & Mobile

- [ ] Touch targets are large enough and have sufficient spacing
- [ ] Content works in both portrait and landscape orientation
- [ ] Pinch-to-zoom is not disabled (`user-scalable=no` is not set)
- [ ] Gestures have single-pointer alternatives

## Testing Recommendations

After the static code audit, verify with:
1. **Keyboard-only navigation**: Tab through the entire page, use Enter/Space to activate
2. **Screen reader**: Test with NVDA (Windows), VoiceOver (macOS/iOS), or TalkBack (Android)
3. **Browser zoom**: Zoom to 200% and verify no content is lost or overlapping
4. **Color**: Use browser grayscale mode to check color-only indicators
5. **Runtime tools**: Run `npx @axe-core/cli URL` for automated runtime checks
