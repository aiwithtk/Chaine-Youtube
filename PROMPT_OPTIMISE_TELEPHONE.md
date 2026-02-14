# 📱 PROMPT POUR PAGE DE VENTE PREMIUM - SMARTPHONE

---

## **ACT AS:**
A world-class Creative Developer (Awwwards/Apple-level) specializing in Next.js, Framer Motion, and immersive 3D web experiences for premium product launches.

---

## **THE TASK:**
Build a high-end "Scrollytelling" sales page for a premium smartphone called **"Apex Pro"**.

**Core Mechanic:** A scroll-linked animation that plays an image sequence of the phone "exploding" (disassembling into components) as the user scrolls down, revealing the internal engineering.

**Business Goal:** Create a premium, Apple-style landing page that converts visitors into buyers through emotional storytelling and technical credibility.

---

## **TECH STACK:**
- **Framework:** Next.js 14 (App Router)
- **Styling:** Tailwind CSS
- **Animation:** Framer Motion
- **Canvas Rendering:** HTML5 Canvas (for 60fps performance)
- **UI Components:** shadcn/ui (for buttons, forms)

---

## **VISUAL DIRECTION & COLOR PALETTE:**

### **Background Matching (CRITICAL):**
- The page background MUST blend seamlessly with the image sequence background
- **Background Color:** `#f5f5f5` (light gray, matches the JPG backgrounds)
- Use eye-dropper tool on `ezgif-frame-001.jpg` to confirm exact hex value if needed

### **Color Scheme:**
- **Primary:** Modern minimalist (inspired by Apple/Samsung)
- **Background:** `bg-[#f5f5f5]` (light mode) 
- **Text:**
  - Headings: `text-zinc-900` (almost black)
  - Body: `text-zinc-700`
  - Accents: `text-amber-600` (matches the bronze phone color)
- **CTA Button:** 
  - Background: `bg-zinc-900`
  - Hover: `bg-amber-600`
  - Text: `text-white`

### **Typography:**
- **Font Family:** Inter or SF Pro Display
- **Headings:** `font-bold tracking-tight text-5xl md:text-7xl`
- **Body:** `font-normal tracking-normal text-lg md:text-xl`
- **Spacing:** Clean, Apple-esque breathing room

---

## **IMPLEMENTATION DETAILS:**

### **1. The "Sticky" Canvas Component**

**File:** `components/PhoneScroll.tsx`

```
Structure:
- Container: h-[500vh] (5x viewport for smooth, slow scroll)
- Canvas: 
  - Position: sticky top-0
  - Size: h-screen w-full
  - Centered with object-fit contain
  - Aspect ratio: 16:9 (1920x1080)
```

**Technical Specs:**
- Canvas must be responsive (scale on mobile)
- Use `requestAnimationFrame` for smooth rendering
- Implement debouncing/throttling if needed (60fps target)

---

### **2. Image Sequence Details**

**Critical Information:**
- **Total Frames:** 40 images
- **Naming Convention:** `ezgif-frame-XXX.jpg` (001 to 040)
- **Resolution:** 1920x1080 pixels (16:9)
- **Format:** JPEG
- **Average Size:** ~30-60KB per image
- **Total Size:** ~1.5-2MB for all frames

**File Location:**
Place images in: `/public/frames/ezgif-frame-001.jpg` to `/public/frames/ezgif-frame-040.jpg`

---

### **3. The Scroll Logic**

**Mapping:**
```javascript
// User scroll progress (0.0 to 1.0) → Frame index (0 to 39)
const scrollProgress = useScroll(...);
const frameIndex = Math.floor(scrollProgress * 39);
const currentFrame = frames[frameIndex];
```

**Preloading Strategy:**
```javascript
// Phase 1: Preload first 10 frames for instant display
// Phase 2: Lazy load remaining 30 frames in background
// Show loading spinner until Phase 1 completes
```

**Performance Requirements:**
- Smooth 60fps animation
- No frame skipping or stuttering
- Use `useTransform` from Framer Motion for interpolation
- Consider using `useSpring` for smoother easing

---

### **4. Text Overlays (The Sales Story)**

**Overlay 1 - Hero (0% Scroll):**
```
Position: Center
Text: "Apex Pro"
Subtext: "Engineering Perfection"
Style: Fade in, massive heading
```

**Overlay 2 - Features (25% Scroll):**
```
Position: Right-aligned
Text: "Triple Camera System"
Subtext: "108MP Main | 12MP Ultra-wide | 5x Telephoto"
Animation: Slide in from right
Note: Phone starts expanding at this point
```

**Overlay 3 - Specs (50% Scroll):**
```
Position: Left-aligned
Text: "A17 Bionic Chip"
Subtext: "5nm Architecture | 6-core CPU | 5-core GPU"
Animation: Slide in from left
Note: Phone is fully exploded, showing motherboard
```

**Overlay 4 - Battery (75% Scroll):**
```
Position: Center
Text: "All-Day Battery"
Subtext: "4800mAh | 65W Fast Charge | Wireless Charging"
Animation: Fade in
Note: Battery component highlighted
```

**Overlay 5 - CTA (90-100% Scroll):**
```
Position: Center
Text: "Own the Future"
Subtext: "Starting at $899"
CTA Button: "Pre-Order Now" → Links to /checkout or modal
Animation: Scale up + glow effect
Note: Phone reassembles or stays exploded
```

---

### **5. Additional Sales Section (Below Scroll Animation)**

After the canvas section, add a traditional sales section:

**Features Grid:**
- 3x2 grid of feature cards
- Icons + short descriptions
- Examples: "Face ID", "IP68 Water Resistant", "5G Connectivity", "ProMotion 120Hz", "Ceramic Shield", "MagSafe Compatible"

**Social Proof:**
- Customer testimonials (3-4)
- Star ratings
- "10,000+ Pre-Orders" badge

**Specs Table:**
- Detailed specifications
- Comparison table (if selling multiple models)

**Final CTA:**
- Large "Add to Cart" button
- Color/Storage selector
- Price breakdown
- Free shipping badge

---

## **6. Polish & UX Enhancements:**

### **Loading State:**
```javascript
// Show elegant loading animation while images preload
// Design: Spinning phone icon or progress bar
// Text: "Loading experience..." 
// Minimum display time: 1 second (even if loaded faster)
```

### **Accessibility:**
```javascript
// Canvas aria-label
<canvas aria-label="Apex Pro smartphone disassembly animation showing internal components" />

// Respect prefers-reduced-motion
@media (prefers-reduced-motion: reduce) {
  // Display static image (frame 20 - mid-explosion)
  // Disable scroll-linked animation
  // Add "Play Animation" button as opt-in
}
```

### **Mobile Optimization:**
- Canvas: Use `object-fit: contain` for proper scaling
- Text overlays: Smaller font sizes on mobile
- Touch-friendly CTA buttons (min 44px height)
- Reduce scroll distance on mobile (300vh instead of 500vh)

### **Performance:**
- Lazy load images below the fold
- Use `IntersectionObserver` for text fade-ins
- Add scroll progress indicator (thin line at top of page)
- Prefetch checkout page on CTA hover

### **Analytics Hooks:**
- Track scroll depth milestones (25%, 50%, 75%, 100%)
- Track CTA clicks
- Track time spent on page

---

## **7. File Structure:**

```
app/
├── page.tsx              // Main landing page
├── globals.css           // Tailwind + custom styles
components/
├── PhoneScroll.tsx       // Main scroll animation component
├── LoadingSpinner.tsx    // Loading state component
├── FeatureCard.tsx       // Individual feature card
├── CTAButton.tsx         // Reusable CTA button
public/
├── frames/
│   ├── ezgif-frame-001.jpg
│   ├── ezgif-frame-002.jpg
│   ├── ...
│   └── ezgif-frame-040.jpg
```

---

## **8. Code Quality Requirements:**

- **TypeScript:** Use strict mode, proper types for all props
- **Comments:** Document complex scroll calculations
- **Error Handling:** Graceful fallback if images fail to load
- **SEO:** 
  - Meta tags for OG image (use frame 001)
  - Structured data for Product schema
  - Alt text for all images
- **Testing:** Test on Chrome, Safari, Firefox, Mobile Safari
- **Performance Budget:** 
  - First Contentful Paint: < 1.5s
  - Time to Interactive: < 3.5s
  - Lighthouse Score: > 90

---

## **EXAMPLE ANIMATION TIMELINE:**

```
Scroll 0%    → Frame 1   → Phone intact (front view, bronze)
Scroll 10%   → Frame 4   → Phone starts to split
Scroll 25%   → Frame 10  → Back cover separates
Scroll 40%   → Frame 16  → Components begin floating
Scroll 50%   → Frame 20  → FULL EXPLOSION (mid-air view)
Scroll 60%   → Frame 24  → Isometric exploded view
Scroll 75%   → Frame 30  → Components spread wide
Scroll 90%   → Frame 36  → Maximum separation
Scroll 100%  → Frame 40  → Final exploded isometric view
```

---

## **DELIVERABLES:**

Generate the following files:

1. **`app/page.tsx`** - Main landing page with sections
2. **`components/PhoneScroll.tsx`** - Canvas animation component
3. **`app/globals.css`** - Tailwind config + custom styles
4. **`components/ui/button.tsx`** - shadcn/ui button component
5. **`README.md`** - Setup instructions + deployment notes

---

## **BONUS FEATURES (If Time Permits):**

- **Sound Design:** Subtle "whoosh" sound on scroll milestones
- **Particle Effects:** Floating dust particles around exploded components
- **Color Variants:** Toggle between Bronze, Silver, Midnight (load different image sequences)
- **AR Preview:** "View in Your Space" button (Apple AR Quick Look)
- **Email Capture:** Newsletter signup with 10% discount code
- **Live Inventory:** "Only 47 left in stock" urgency badge

---

## **INSPIRATION REFERENCES:**

- Apple iPhone launch pages
- Samsung Galaxy Unpacked sites
- Awwwards "Site of the Day" winners
- Active Theory portfolio work
- Vercel and Linear landing pages (for minimalism)

---

## **FINAL NOTES:**

This is a **premium sales experience**, not just a demo. Every interaction should feel buttery smooth, intentional, and luxurious. The goal is to make visitors think "I NEED to own this phone" through emotional design and technical storytelling.

Prioritize:
1. **Performance** (smooth 60fps)
2. **Aesthetics** (Apple-level polish)
3. **Conversion** (clear CTA, trust signals)
4. **Accessibility** (works for everyone)

Good luck building something Awwwards-worthy! 🚀
