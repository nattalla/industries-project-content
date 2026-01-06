# Screenshot to Blocks - Skill Module

## CRITICAL LESSONS LEARNED

**WHAT DOESN'T WORK:**
1. ❌ Using `greenshift-blocks/row`, `greenshift-blocks/heading`, `greenshift-blocks/button` - these may not be available in user's GreenShift installation
2. ❌ Adding inline `style=""` attributes to force colors - GreenShift ignores these
3. ❌ Using nested spacing objects like `"spacing":{"padding":{"values":{...}}}` - causes "Cannot read properties of undefined" errors
4. ❌ Being overly positive about code that looks broken on the live site
5. ❌ Using specific image URLs from screenshots - use placeholder services instead

**WHAT WORKS:**
1. ✅ Use `greenshift-blocks/element` - proven to exist in user's installation
2. ✅ Colors go in `styleAttributes` arrays: `"color":["#ffffff"]` NOT inline styles
3. ✅ Use direct properties: `"paddingTop":["60px"]` NOT nested spacing objects
4. ✅ Use `\u002d` encoding for dashes in CSS variables
5. ✅ Include `align="full"`, `isVariation`, and `metadata` attributes for proper validation
6. ✅ Use placeholder image services like `https://via.placeholder.com/1920x800/4B7878/4B7878` or WordPress default gray box
7. ✅ Accept that one "Attempt Recovery" click is normal and acceptable

**PLACEHOLDER IMAGES:**
- Use `https://via.placeholder.com/[width]x[height]/[bgcolor]/[bgcolor]` for solid color placeholders
- Example: `https://via.placeholder.com/1920x800/4B7878/4B7878` for Rooted teal background
- Or let WordPress use default gray placeholder box

## INSTRUCTIONS FOR CLAUDE

When the user uploads a screenshot and asks to convert it to blocks:

1. **Analyze the screenshot** using the workflow in this document
2. **Default to WP Core blocks** - simpler and more reliable
3. **Use GreenShift ONLY with `greenshift-blocks/element`** - other GS block types may not be available
4. **Extract actual content from screenshot** - no generic placeholders
5. **Use placeholder images** from reliable services, NOT specific URLs from screenshots
6. **Follow the EXACT pattern from working testimonials code** for GreenShift
7. **Test mentally before outputting** - does this look right on a live site?

**CRITICAL:** Output must be WordPress block HTML code with `<!-- wp:` comments, NOT standalone CSS or HTML.

**CRITICAL:** One "Attempt Recovery" click is expected and acceptable. Focus on ensuring code works AFTER recovery.

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

**Generic â†’ Rooted Translation:**
- Purple/Blue accents â†’ `#4B7878` or `#5E9797`
- Light backgrounds â†’ `#E1F0F0` or `#f5f7f7`
- Dark text â†’ `#1b2b2b`
- Medium gray text â†’ `#3b5e5e` or `#5E9797`

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
    <!-- wp:button {"backgroundColor":"primary","textColor":"white","style":{"border":{"radius":"4px"},"typography":{"fontSize":"14px","fontWeight":"600"}}} -->
    <div class="wp-block-button"><a class="wp-block-button__link has-white-color has-primary-background-color has-text-color has-background wp-element-button" style="border-radius:4px;font-size:14px;font-weight:600" href="#top">CATEGORY</a></div>
    <!-- /wp:button -->
    
    <!-- wp:button {"backgroundColor":"white","textColor":"primary","className":"is-style-outline","style":{"border":{"radius":"4px","width":"2px"},"typography":{"fontSize":"14px","fontWeight":"600"}}} -->
    <div class="wp-block-button is-style-outline"><a class="wp-block-button__link has-primary-color has-white-background-color has-text-color has-background wp-element-button" style="border-radius:4px;border-width:2px;font-size:14px;font-weight:600" href="#top">Tag</a></div>
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
- Responsive font sizes: Desktop (56px) â†’ Tablet (48px) â†’ Mobile (36px)
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
    â”œâ”€> Simple layout? (headings, text, buttons)
    â”‚       â””â”€> Use WP Core Blocks
    â”‚
    â”œâ”€> Needs responsive sizing?
    â”‚       â””â”€> Use GreenShift Elements
    â”‚
    â”œâ”€> Complex layout? (grids, flexbox, precise spacing)
    â”‚       â””â”€> Use GreenShift Elements
    â”‚
    â””â”€> Not sure?
            â””â”€> Provide both versions, explain trade-offs
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

### Issue: "Cannot read properties of undefined (reading 'values')" error
**Cause:** Using nested spacing objects like `"spacing":{"padding":{"values":{...}}}`
**Solution:** Use direct properties: `"paddingTop":["60px"]` instead

### Issue: Colors not applying correctly
**Cause:** Using inline `style=""` attributes that GreenShift ignores
**Solution:** Put colors in `styleAttributes` arrays: `"color":["#ffffff"]`

### Issue: "Block contains unexpected or invalid content" error
**Cause:** Using GreenShift block types that don't exist in user's installation (like `greenshift-blocks/row`)
**Solution:** Only use `greenshift-blocks/element` for GreenShift blocks

### Issue: Code doesn't paste correctly
**Solution:** 
1. Switch to Code Editor mode first
2. Clear any existing content
3. Paste code
4. Switch back to Visual Editor
5. Expect one "Attempt Recovery" click - this is normal

### Issue: Heading shows "Resolve Block" dialog
**Cause:** WordPress wants to add `wp-block-heading` class
**Solution:** Click "Convert to Blocks" - it will work perfectly after conversion

### Issue: Button looks terrible on live site
**Cause:** Not using proper button styling attributes
**Solution:** Include `boxShadow`, proper `backgroundColor`, `color`, and `borderRadius` in styleAttributes

### Issue: Background image not showing
**Cause:** Using invalid URL or wrong CSS property
**Solution:** Use `"backgroundImage":["url(https://via.placeholder.com/...)"]` with valid placeholder URL

### Issue: Overlay too dark or wrong opacity
**Cause:** Using wrong rgba value
**Solution:** Use `"backgroundColor":["rgba(0,0,0,0.4)"]` for 40% dark overlay (adjust 0.4 value as needed)

---

## Best Practices

1. **Start simple**: Use WP Core unless you have a specific reason not to
2. **Test responsive**: Check desktop, tablet, mobile views before finalizing
3. **Brand consistency**: Always use Rooted's color palette
4. **Semantic HTML**: Use proper heading hierarchy (H1 â†’ H2 â†’ H3)
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

### Example 3: Hero Section with Background (Proven Working)
**Use case:** Full-width hero section with background image, overlay, heading, text, and CTA
**Approach:** GreenShift Element (tested and working after one recovery click)
**Code:**

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-hero-section","tag":"section","type":"inner","localId":"gsbp-hero-section","align":"full","styleAttributes":{"display":["flex"],"justifyContent":["center"],"flexDirection":["column"],"alignItems":["center"],"paddingRight":["var(\u002d\u002dwp\u002d\u002dcustom\u002d\u002dspacing\u002d\u002dside, min(3vw, 20px))"],"paddingLeft":["var(\u002d\u002dwp\u002d\u002dcustom\u002d\u002dspacing\u002d\u002dside, min(3vw, 20px))"],"marginTop":["0px"],"marginBottom":["0px"],"paddingLink_Extra":"lr","position":["relative"],"backgroundImage":["url(https://via.placeholder.com/1920x800/4B7878/4B7878)"],"backgroundSize":["cover"],"backgroundPosition":["center"],"paddingTop":["80px","60px","40px"],"paddingBottom":["80px","60px","40px"],"minHeight":["500px","400px","350px"]},"isVariation":"contentcolumns"} -->
<section class="gsbp-hero-section alignfull"><!-- wp:greenshift-blocks/element {"id":"gsbp-hero-overlay","type":"inner","localId":"gsbp-hero-overlay","styleAttributes":{"position":["absolute"],"top":["0"],"left":["0"],"right":["0"],"bottom":["0"],"backgroundColor":["rgba(0,0,0,0.4)"],"zIndex":["1"]}} -->
<div class="gsbp-hero-overlay"></div>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-hero-content","type":"inner","localId":"gsbp-hero-content","styleAttributes":{"maxWidth":["100%"],"width":["var(\u002d\u002dwp\u002d\u002dstyle\u002d\u002dglobal\u002d\u002dwide-size, 800px)"],"position":["relative"],"zIndex":["2"],"display":["flex"],"flexDirection":["column"],"alignItems":["flex-start"],"rowGap":["30px"]},"isVariation":"nocolumncontent","metadata":{"name":"Content Area"}} -->
<div class="gsbp-hero-content"><!-- wp:greenshift-blocks/element {"id":"gsbp-hero-h1","tag":"h1","localId":"gsbp-hero-h1","textContent":"Your Heading Here","styleAttributes":{"fontSize":["56px","48px","36px"],"fontWeight":["700"],"lineHeight":["1.2"],"color":["#ffffff"],"marginTop":["0px"],"marginBottom":["0px"]}} -->
<h1 class="gsbp-hero-h1">Your Heading Here</h1>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-hero-p","tag":"p","localId":"gsbp-hero-p","textContent":"Your description text goes here. This should be extracted from the screenshot.","styleAttributes":{"fontSize":["18px","17px","16px"],"lineHeight":["1.6"],"color":["#ffffff"],"marginTop":["0px"],"marginBottom":["0px"]}} -->
<p class="gsbp-hero-p">Your description text goes here. This should be extracted from the screenshot.</p>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-hero-btn","tag":"a","localId":"gsbp-hero-btn","href":"#top","textContent":"Button Text","styleAttributes":{"display":["inline-block"],"paddingTop":["14px"],"paddingBottom":["14px"],"paddingLeft":["32px"],"paddingRight":["32px"],"backgroundColor":["#ffffff"],"color":["#1b2b2b"],"borderRadius":["4px"],"fontSize":["16px"],"fontWeight":["600"],"textDecoration":["none"],"boxShadow":["0 2px 8px rgba(0,0,0,0.15)"]}} -->
<a class="gsbp-hero-btn" href="#top">Button Text</a>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element --></section>
<!-- /wp:greenshift-blocks/element -->
```

**Key Points:**
- Uses `\u002d` encoding for CSS variables
- Colors in `styleAttributes` arrays, NOT inline styles
- Direct properties like `paddingTop` NOT nested objects
- Placeholder image from reliable service
- One recovery click expected and acceptable
- Works perfectly after recovery

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

---

## UPDATED BEST PRACTICES (January 2026)

Based on actual testing and failures:

1. **Default to WP Core**: Use WordPress Core blocks unless you specifically need responsive font sizing
2. **For GreenShift, use ONLY `greenshift-blocks/element`**: Other block types may not be available in user's installation
3. **Extract actual content from screenshot**: Get real text, don't use generic placeholders like "Your heading here"
4. **Use reliable placeholder images**: `https://via.placeholder.com/[width]x[height]/[bgcolor]/[bgcolor]` - Example: `https://via.placeholder.com/1920x800/4B7878/4B7878`
5. **Colors go in styleAttributes arrays**: `"color":["#ffffff"]` - NEVER use inline `style=""` attributes
6. **Accept one recovery click as normal**: "Attempt Recovery" prompt is expected and acceptable if code works after clicking
7. **Test code mentally before outputting**: Visualize if colors, spacing, and layout will look right on live site
8. **Follow proven patterns exactly**: Use the testimonials code structure for GreenShift blocks
9. **Use direct CSS properties**: `"paddingTop":["60px"]` NOT nested objects like `"spacing":{"padding":{"values":{...}}}`
10. **Use Unicode encoding for CSS variables**: `\u002d` instead of `-` in variable names

## WHAT TO AVOID

- ❌ Never use `greenshift-blocks/row`, `greenshift-blocks/heading`, `greenshift-blocks/button` - may not exist
- ❌ Never add inline `style=""` attributes to force colors - GreenShift ignores them
- ❌ Never use nested spacing objects - causes JavaScript errors
- ❌ Never be overly positive about code that looks broken on the live site
- ❌ Never use specific image URLs from screenshots - use placeholder services
- ❌ Never assume code works without seeing the live result

