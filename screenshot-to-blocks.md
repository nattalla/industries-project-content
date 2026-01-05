# Screenshot to Blocks - Skill Module

## INSTRUCTIONS FOR CLAUDE

When the user uploads a screenshot and asks to convert it to blocks:

1. **Analyze the screenshot** using the workflow in this document
2. **Decide** whether to use WP Core or GreenShift blocks (default to Core)
3. **Translate colors** to Rooted's brand palette (see Brand Translation section)
4. **Generate block code** in WordPress block format (not CSS)
5. **Provide working code** the user can copy directly into WordPress Code Editor
6. **Reference the Proven Example** for code structure and formatting
7. **Offer both versions** (Core and GreenShift) when appropriate

**CRITICAL:** Output must be WordPress block HTML code with `<!-- wp:` comments, NOT standalone CSS or HTML.

**OUTPUT FORMAT:**
```html
<!-- wp:group {...} -->
<div class="wp-block-group">
  <!-- Actual block code here -->
</div>
<!-- /wp:group -->
```

## Purpose
Convert design screenshots into working WordPress block code that matches Rooted's brand, is responsive, and uses the appropriate blocks (WP Core vs GreenShift).

---

## The Workflow

### Step 1: Analyze the Screenshot
When user uploads a screenshot, identify:
- **Structure elements**: Headers, sections, containers
- **Content elements**: Headings, paragraphs, buttons, chips/tags
- **Visual hierarchy**: What's primary, secondary, tertiary
- **Spacing**: Padding, margins, gaps between elements
- **Typography**: Font sizes, weights, line heights
- **Colors**: Backgrounds, text, accents
- **Responsive needs**: Does it need breakpoints?

### Step 2: Decide: WP Core or GreenShift?

**Use WP Core Blocks when:**
- Simple layout (headings, paragraphs, buttons)
- Static font sizes work fine
- No complex responsive breakpoints needed
- Speed/simplicity is priority
- Standard WordPress components

**Use GreenShift Blocks when:**
- Need responsive font sizes (desktop/tablet/mobile)
- Complex layouts with precise control
- Custom spacing that varies by breakpoint
- Advanced styling (animations, transforms, etc.)
- Need element-level control

**Default to WP Core unless there's a specific reason to use GreenShift.**

### Step 3: Brand Translation
Replace screenshot colors with Rooted's palette:

**Rooted Brand Colors:**
- Primary Teal: `#4B7878`
- Secondary Teal: `#5E9797`
- Light Teal: `#92BBBB`
- Background Teal 1: `#E1F0F0`
- Background Teal 2: `#EFF7F7`
- Dark Text: `#1b2b2b`
- Medium Gray: `#3b5e5e`

**Generic → Rooted Translation:**
- Purple/Blue accents → `#4B7878` or `#5E9797`
- Light backgrounds → `#E1F0F0` or `#f5f7f7`
- Dark text → `#1b2b2b`
- Medium gray text → `#3b5e5e` or `#5E9797`

### Step 4: Build the Code

**Template structure:**
1. Outer container (Group or GS Element with section tag)
2. Content wrapper (constrained width, centered)
3. Content elements (chips, headings, text, etc.)
4. Proper spacing and typography
5. Responsive considerations

### Step 5: Provide Both Versions (if applicable)

When the layout could work with either:
- Give WP Core version first (simpler)
- Offer GreenShift alternative (more control)
- Explain trade-offs

---

## Proven Example: Article Header

### Original Request
User shared screenshot of article header with:
- Category chips/tags (purple accent)
- Large heading
- Subtitle/description
- Date stamp
- Light gray background

### WP Core Version

```html
<!-- wp:group {"style":{"spacing":{"padding":{"top":"60px","bottom":"60px","left":"var(--wp--custom--spacing--side, 20px)","right":"var(--wp--custom--spacing--side, 20px)"}},"color":{"background":"#E1F0F0"}},"layout":{"type":"constrained","contentSize":"1200px"}} -->
<div class="wp-block-group has-background" style="background-color:#E1F0F0;padding-top:60px;padding-bottom:60px;padding-left:var(--wp--custom--spacing--side, 20px);padding-right:var(--wp--custom--spacing--side, 20px)">
  
  <!-- Category Chips -->
  <!-- wp:buttons {"style":{"spacing":{"blockGap":"15px"}}} -->
  <div class="wp-block-buttons">
    <!-- wp:button {"style":{"border":{"radius":"4px"},"typography":{"fontSize":"14px","fontWeight":"600","textTransform":"uppercase","letterSpacing":"0.5px"},"color":{"background":"#4B7878","text":"#ffffff"}}} -->
    <div class="wp-block-button"><a class="wp-block-button__link has-text-color has-background wp-element-button" style="border-radius:4px;background-color:#4B7878;color:#ffffff;font-size:14px;font-weight:600;letter-spacing:0.5px;text-transform:uppercase" href="/category">CATEGORY</a></div>
    <!-- /wp:button -->
    
    <!-- wp:button {"className":"is-style-outline","style":{"typography":{"fontSize":"14px","fontWeight":"600"},"color":{"text":"#4B7878"}}} -->
    <div class="wp-block-button is-style-outline"><a class="wp-block-button__link has-text-color wp-element-button" style="color:#4B7878;font-size:14px;font-weight:600" href="/tag">Tag</a></div>
    <!-- /wp:button -->
  </div>
  <!-- /wp:buttons -->
  
  <!-- Main Heading -->
  <!-- wp:heading {"level":1,"style":{"typography":{"fontSize":"56px","fontWeight":"700","lineHeight":"1.2","letterSpacing":"-0.5px"},"spacing":{"margin":{"top":"30px","bottom":"30px"}},"color":{"text":"#1b2b2b"}}} -->
  <h1 class="wp-block-heading has-text-color" style="color:#1b2b2b;margin-top:30px;margin-bottom:30px;font-size:56px;font-weight:700;letter-spacing:-0.5px;line-height:1.2">Your Headline Goes Here</h1>
  <!-- /wp:heading -->
  
  <!-- Subtitle/Description -->
  <!-- wp:paragraph {"style":{"typography":{"fontSize":"22px","lineHeight":"1.5"},"spacing":{"margin":{"top":"0","bottom":"25px"}},"color":{"text":"#5E9797"}}} -->
  <p class="has-text-color" style="color:#5E9797;margin-top:0;margin-bottom:25px;font-size:22px;line-height:1.5">Your subtitle or description goes here. Keep it concise and engaging.</p>
  <!-- /wp:paragraph -->
  
  <!-- Date/Meta Info -->
  <!-- wp:paragraph {"style":{"typography":{"fontSize":"16px"},"color":{"text":"#5E9797"},"spacing":{"margin":{"top":"0","bottom":"0"}}}} -->
  <p class="has-text-color" style="color:#5E9797;margin-top:0;margin-bottom:0;font-size:16px">December 10, 2025</p>
  <!-- /wp:paragraph -->
</div>
<!-- /wp:group -->
```

**Strengths:**
- Simple, clean code
- Fast to implement
- Easy to customize
- Works across all themes

**Limitations:**
- Fixed font sizes (doesn't scale for mobile)
- Less granular control
- Manual adjustments needed for responsive

---

### GreenShift Version

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-article-header","tag":"section","type":"inner","localId":"gsbp-article-header","styleAttributes":{"paddingTop":["60px"],"paddingBottom":["60px"],"paddingLeft":["var(--wp--custom--spacing--side, min(3vw, 20px))"],"paddingRight":["var(--wp--custom--spacing--side, min(3vw, 20px))"],"backgroundColor":["#E1F0F0"]}} -->
<section class="gsbp-article-header">
  <!-- wp:greenshift-blocks/element {"id":"gsbp-content-wrapper","type":"inner","localId":"gsbp-content-wrapper","styleAttributes":{"maxWidth":["1200px"],"marginLeft":["auto"],"marginRight":["auto"]}} -->
  <div class="gsbp-content-wrapper">
    
    <!-- Category Tags -->
    <!-- wp:greenshift-blocks/element {"id":"gsbp-category-tags","type":"inner","localId":"gsbp-category-tags","styleAttributes":{"display":["flex"],"gap":["15px"],"marginBottom":["30px"],"flexWrap":["wrap"]}} -->
    <div class="gsbp-category-tags">
      <!-- wp:greenshift-blocks/element {"id":"gsbp-tag-primary","textContent":"CATEGORY","tag":"span","localId":"gsbp-tag-primary","styleAttributes":{"backgroundColor":["#4B7878"],"color":["#ffffff"],"paddingTop":["8px"],"paddingBottom":["8px"],"paddingLeft":["20px"],"paddingRight":["20px"],"borderRadius":["4px"],"fontSize":["14px"],"fontWeight":["600"],"textTransform":["uppercase"],"letterSpacing":["0.5px"]}} -->
      <span class="gsbp-tag-primary">CATEGORY</span>
      <!-- /wp:greenshift-blocks/element -->
      
      <!-- wp:greenshift-blocks/element {"id":"gsbp-tag-secondary","textContent":"Tag","tag":"span","localId":"gsbp-tag-secondary","styleAttributes":{"backgroundColor":["transparent"],"color":["#4B7878"],"paddingTop":["8px"],"paddingBottom":["8px"],"paddingLeft":["20px"],"paddingRight":["20px"],"fontSize":["14px"],"fontWeight":["600"]}} -->
      <span class="gsbp-tag-secondary">Tag</span>
      <!-- /wp:greenshift-blocks/element -->
    </div>
    <!-- /wp:greenshift-blocks/element -->
    
    <!-- Main Heading with Responsive Sizing -->
    <!-- wp:greenshift-blocks/element {"id":"gsbp-headline","textContent":"Your Headline Goes Here","tag":"h1","localId":"gsbp-headline","styleAttributes":{"fontSize":["56px","48px","36px"],"fontWeight":["700"],"lineHeight":["1.2"],"color":["#1b2b2b"],"marginTop":["0px"],"marginBottom":["30px"],"letterSpacing":["-0.5px"]}} -->
    <h1 class="gsbp-headline">Your Headline Goes Here</h1>
    <!-- /wp:greenshift-blocks/element -->
    
    <!-- Subtitle with Responsive Sizing -->
    <!-- wp:greenshift-blocks/element {"id":"gsbp-subtitle","textContent":"Your subtitle or description goes here. Keep it concise and engaging.","tag":"p","localId":"gsbp-subtitle","styleAttributes":{"fontSize":["22px","20px","18px"],"lineHeight":["1.5"],"color":["#5E9797"],"marginTop":["0px"],"marginBottom":["25px"]}} -->
    <p class="gsbp-subtitle">Your subtitle or description goes here. Keep it concise and engaging.</p>
    <!-- /wp:greenshift-blocks/element -->
    
    <!-- Date/Meta -->
    <!-- wp:greenshift-blocks/element {"id":"gsbp-date","textContent":"December 10, 2025","tag":"p","localId":"gsbp-date","styleAttributes":{"fontSize":["16px"],"color":["#5E9797"],"marginTop":["0px"],"marginBottom":["0px"]}} -->
    <p class="gsbp-date">December 10, 2025</p>
    <!-- /wp:greenshift-blocks/element -->
    
  </div>
  <!-- /wp:greenshift-blocks/element -->
</section>
<!-- /wp:greenshift-blocks/element -->
```

**Strengths:**
- Responsive font sizes: Desktop (56px) → Tablet (48px) → Mobile (36px)
- Precise control over every element
- Better mobile experience out of the box
- Semantic HTML (section, spans)

**Limitations:**
- More complex code
- Requires GreenShift plugin
- Harder to hand-edit later

---

## Common Adjustments

### Typography Scaling
**Problem:** Headings too large on mobile
**Solution:** Use GreenShift's responsive arrays
```
"fontSize":["56px","48px","36px"]  // Desktop, Tablet, Mobile
```

### Spacing Issues
**Problem:** Too much padding on mobile
**Solution:** Use CSS variables or responsive arrays
```
"paddingLeft":["60px","40px","20px"]  // Scales down
```

### Color Consistency
**Problem:** Colors don't match Rooted brand
**Solution:** Always use Rooted's color palette

**Quick reference:**
- Buttons/CTAs: `#4B7878` background, `#ffffff` text
- Headings: `#1b2b2b`
- Body text: `#3b5e5e`
- Accents/links: `#5E9797`
- Light backgrounds: `#E1F0F0` or `#EFF7F7`

---

## Decision Tree

```
Screenshot uploaded
    |
    ├─> Simple layout? (headings, text, buttons)
    │       └─> Use WP Core Blocks
    │
    ├─> Needs responsive sizing?
    │       └─> Use GreenShift Elements
    │
    ├─> Complex layout? (grids, flexbox, precise spacing)
    │       └─> Use GreenShift Elements
    │
    └─> Not sure?
            └─> Provide both versions, explain trade-offs
```

---

## Common Patterns

### 1. Hero/Header Section
**Elements:** Background, centered content, heading, subheading, CTA
**Best approach:** WP Core Group + Buttons
**When to use GS:** Need responsive heading sizes

### 2. Category Chips/Tags
**Elements:** Multiple small buttons/labels
**Best approach:** WP Core Buttons block with custom styling
**When to use GS:** Need precise flexbox control, custom gap sizing

### 3. Content Cards
**Elements:** Image, heading, excerpt, link
**Best approach:** WP Core Columns or GreenShift Container
**When to use GS:** Need consistent card heights, advanced hover effects

### 4. Stats/Numbers Section
**Elements:** Large numbers, labels, icons
**Best approach:** GreenShift Elements (better number sizing control)
**When to use Core:** Simple stats with standard sizing

---

## Troubleshooting

### Issue: Code doesn't paste correctly
**Solution:** 
1. Switch to Code Editor mode first
2. Clear any existing content
3. Paste code
4. Switch back to Visual Editor

### Issue: Colors look wrong
**Solution:** Check if theme is overriding styles
- Use inline `style` attributes instead of classes when possible
- Or add `!important` to critical styles

### Issue: Responsive sizing not working
**Solution:** 
- Core blocks: Add media queries manually or use theme's responsive settings
- GreenShift: Verify array syntax: `["desktop","tablet","mobile"]`

### Issue: Spacing inconsistent
**Solution:**
- Use CSS variables for consistency: `var(--wp--custom--spacing--side, 20px)`
- Or hardcode specific values for precise control

---

## Best Practices

1. **Start simple**: Use WP Core unless you have a specific reason not to
2. **Test responsive**: Check desktop, tablet, mobile views before finalizing
3. **Brand consistency**: Always use Rooted's color palette
4. **Semantic HTML**: Use proper heading hierarchy (H1 → H2 → H3)
5. **Accessibility**: Include proper ARIA labels, color contrast
6. **Performance**: Fewer blocks = faster page load

---

## Quick Checklist

Before delivering code:
- [ ] Correct blocks chosen (Core vs GreenShift)
- [ ] Rooted brand colors applied
- [ ] Responsive sizing considered
- [ ] Spacing/padding appropriate
- [ ] Typography hierarchy correct
- [ ] Semantic HTML tags used
- [ ] Code formatted and commented
- [ ] Both versions provided (if applicable)

---

## Examples Library

### Example 1: Simple CTA Section
**Use case:** Call-to-action at bottom of page
**Approach:** WP Core Group + Heading + Button
**Code:** [See WP Core template above]

### Example 2: Article Header (Proven)
**Use case:** Blog post or article intro
**Approach:** Both versions work
**Code:** [See both versions above]

### Example 3: Service Card Grid
**Use case:** Services page with 4 service cards
**Approach:** GreenShift Query + Container (if dynamic) or Core Columns (if static)
**Code:** [To be added when needed]

---

## Notes

- This module documents the proven workflow from the purple screenshot example
- Default to WP Core blocks for simplicity
- Use GreenShift when responsive control is critical
- Always translate colors to Rooted's brand palette
- Provide both versions when applicable
- Test on actual site before finalizing

---

## Related Skills

- `acf-greenshift-setup.md` - Connecting ACF fields to GreenShift blocks
- `fix-responsive-issues.md` - Troubleshooting mobile layouts
- `typography-sizing-guide.md` - Fluid vs fixed font sizing
