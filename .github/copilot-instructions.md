# Copilot Instructions: Portfolio Project

## Project Overview
This is a personal portfolio website for Kanishka Shrivastava, a Java engineer. It's a single-page application (SPA) built with vanilla HTML/CSS/JavaScript, featuring a premium dark-themed design with interactive 3D effects and smooth scroll animations.

**Key Tech Stack:**
- HTML5 (structure)
- CSS3 with CSS Variables (styling & theming)
- Vanilla JavaScript (interactions)
- No frameworks or build tools

## Architecture & Design Patterns

### CSS Organization
- **CSS Variables (`:root` & `.light`)**: Theme switching system uses two color palettes defined in `:root` for dark mode and `.light` for light mode
- **Single stylesheet**: All styles embedded in `<style>` tag within `index.html`
- **Key variables to know**: `--bg`, `--text`, `--glass` (glassmorphism), `--grad` (gradient colors)

### JavaScript Interactions
All functionality is in the `<script>` section at document end:

1. **Typing effect** (`typing()` function): Animates the role text character-by-character with 60ms delay
2. **Scroll reveal** (`IntersectionObserver`): Adds `.show` class to sections when 20% visible, triggering CSS transitions
3. **Theme toggle** (`toggleTheme()`): Adds/removes `.light` class on body
4. **Mobile menu** (`toggleMenu()`): Toggles `.show-menu` on nav to show/hide links
5. **3D cursor** (`mousemove` on `.cursor3d`): Custom cursor with red/cyan anaglyph 3D effect
6. **Orb parallax** (`mousemove` on `.orb`): Background orb moves based on mouse position (30px max)
7. **Card tilt** (`mousemove` on cards): 3D perspective transform based on mouse position within card

### Component Structure
- **Navigation**: Fixed bar at top with theme toggle and hamburger menu (hidden on desktop, shown <900px)
- **Sections**: `hero`, `about`, `projects`, `resume`, `contact` - all use scroll-triggered opacity/transform
- **Cards**: Reusable `.card` component with glass morphism and hover tilt effects

## Working with the Code

### Making Changes
- **Theme colors**: Update `--bg`, `--text`, `--grad` in `:root` (dark) or `.light` (light)
- **Animations**: Keyframes `float` and `float-photo` in CSS; timing hardcoded in JS functions (e.g., 60ms for typing)
- **Mobile breakpoint**: `@media(max-width:900px)` at end of styles - adjust nav/orb sizing here

### Adding New Sections
1. Add `<section id="your-id">` block in HTML
2. Use `.show` trigger (already hooked up via IntersectionObserver)
3. Apply `.card` class for consistent styling
4. Add link to nav if needed

### Updating Content
- **Profile photo**: Reference at `<img src="profile.jpg" alt="...">` (line ~350)
- **Resume download**: Links to `resume.pdf` in two places (buttons) - add this file to enable
- **Project cards**: Edit in `.grid` div with `<h4>`, `<p>`, and `<small>` tags for tech stack

## Conventions & Patterns

- **No external libraries**: All vanilla JS - keep it lightweight
- **CSS-first effects**: Leverage CSS transitions/transforms over JS animations where possible
- **Accessibility**: Custom cursor now respects `prefers-reduced-motion` and has proper fallbacks
- **Performance-first**: GPU-heavy effects (blur) reduced for motion-sensitive users
- **Form integration**: Uses Formspree (https://formspree.io) for contact submissions - update form ID if needed
- **Inline styles**: All CSS in single sheet; only runtime styles applied via JS

## Build & Deployment

- **No build step**: Open `index.html` directly in browser
- **Deployment**: Already deployed to GitHub Pages at https://kanishkashrivastava07.github.io/Portfolio/
- **Performance note**: Blur effects on `.bg` and `.orb` are GPU-heavy - test on lower-end devices

## Known Issues & TODOs

- ✅ **Assets**: Profile photo (`profile.jpg`) now correctly referenced
- ✅ **Contact form**: Now fully functional with Formspree integration
- ✅ **Accessibility**: Custom cursor respects `prefers-reduced-motion`, ARIA labels added to nav
- ✅ **Performance**: Blur effects and animations reduced for motion-sensitive users
- **Resume PDF**: Add `resume.pdf` file when ready to enable download functionality

## Recent Improvements (v2.0)

1. **Fixed profile photo**: Updated from placeholder `your-photo.png` to `profile.jpg`
2. **Functional contact form**: Integrated Formspree (no backend needed) with required validation
3. **Accessibility enhancements**:
   - Custom 3D cursor now respects `prefers-reduced-motion` media query
   - Added ARIA labels to theme toggle and mobile menu
   - Added `role="button"` and `tabindex="0"` for keyboard navigation
4. **Performance optimizations**:
   - Reduced blur filter strength for users with motion preferences
   - Disabled animations for reduced-motion preferences
   - Fade out orb element instead of animating it
5. **Enhanced project section**: 
   - Expanded project descriptions with real-world details
   - Added technology tags for each project (`<small>` tags)
   - Better visual hierarchy with styled project metadata
