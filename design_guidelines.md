# Design Guidelines: Multi-Agent Web Development Platform

## Design Approach
**Reference-Based:** Drawing inspiration from modern developer tools like Linear, Vercel, and GitHub's dark interfaces, combined with the OpenHands aesthetic shown in the reference images.

## Core Visual Identity

### Color Palette
- **Primary Background:** Deep charcoal/near-black (#0F0F0F to #1A1A1A)
- **Card/Surface Background:** Dark gray (#1E1E1E to #252525)
- **Accent Color:** Warm gold/amber (#F59E0B to #FBBF24) for primary actions
- **Text Hierarchy:** White (#FFFFFF) for headings, light gray (#E5E5E5) for body, muted gray (#A3A3A3) for secondary text
- **Borders:** Subtle dark borders (#2A2A2A to #333333)

### Typography
- **Primary Font:** Inter or similar modern sans-serif via Google Fonts
- **Heading Sizes:** text-3xl to text-4xl for main headings, text-xl for card titles, text-lg for modal headers
- **Body Text:** text-base with adequate line-height (1.6-1.8)
- **Font Weights:** 600-700 for headings, 500 for labels, 400 for body text

### Layout System
**Spacing Units:** Primarily use Tailwind units of 4, 6, 8, 12, 16, and 24 (p-4, gap-6, mb-8, etc.)

## Component Library

### Authentication Modal
- **Size:** Medium-width centered modal (max-w-md)
- **Background:** Card background color with subtle border
- **Padding:** p-8 for content area
- **Header:** Bold text-xl with toggle between "Login" and "Sign Up" as text links
- **OAuth Buttons:** Full-width buttons with provider logos, dark gray background (#2A2A2A), white text
- **Divider:** Horizontal line with "OR" text centered
- **Input Fields:** Dark background (#1A1A1A), light border, rounded corners, p-3 padding
- **Primary CTA:** Gold/amber button, full-width, rounded, py-3
- **Backdrop:** Semi-transparent black overlay (#000000 with 60-70% opacity)

### Landing Page (Unauthenticated)
- **Hero Section:** 70vh minimum height, centered content
- **Headline:** Large, bold text (text-4xl to text-5xl), white color
- **Subheading:** text-lg to text-xl, muted gray color
- **CTA Buttons:** Prominent gold button triggering authentication modal

### Dashboard (Authenticated)

**Left Sidebar:**
- **Width:** Fixed w-64 on desktop, collapsible on mobile
- **Icons:** Use Heroicons, consistent 24px size
- **Active State:** Gold accent border-left (4px) with lighter background
- **Navigation Items:** Vertical stack with gap-2, p-3 padding each

**Main Content Area:**
- **Header:** "Let's Start Building!" as text-3xl, mb-12
- **Action Cards:** 2-column grid (grid-cols-1 lg:grid-cols-2), gap-6
  - **Card Design:** Dark gray background, rounded-xl, border, p-8 padding
  - **Icon/Illustration Area:** Top section with 80px height placeholder
  - **Card Title:** text-xl, bold, mb-3
  - **Card Description:** text-base, muted gray, mb-6
  - **Card CTA:** Gold button or text link with arrow icon

**Open Repository Card:**
- Input field for repository URL
- Dropdown for branch selection
- Gold "Continue" button

**Start from Scratch Card:**
- Brief description text
- Gold "New Conversation" button

**Recent Conversations Section:**
- **Header:** text-xl, mb-6
- **List Items:** Dark cards with hover state (slight brightness increase)
- **Item Structure:** Project name (bold), timestamp (small, muted), truncated description

**Suggested Tasks Section:**
- **Grid Layout:** 3 columns on desktop (grid-cols-1 md:grid-cols-2 lg:grid-cols-3)
- **Task Cards:** Smaller, compact design with icon, title, and brief description
- **Hover Effect:** Subtle border glow using gold accent

## Animations
- **Modal Entrance:** Fade-in with subtle scale (0.95 to 1.0), 200ms duration
- **Button Hovers:** Slight brightness increase (110%), 150ms transition
- **Card Hovers:** Translate up by 2px, add subtle shadow, 200ms transition

## Images
No hero images for this application. Focus on iconography using Heroicons throughout. Use simple geometric shapes or subtle gradient backgrounds where visual interest is needed (e.g., authentication modal backdrop).

## Accessibility
- High contrast ratios (white text on dark backgrounds meets WCAG AA)
- Focus states with gold outline (2px, visible on all interactive elements)
- Proper heading hierarchy (h1 for main page title, h2 for sections, h3 for cards)
- Descriptive aria-labels for icon-only buttons
- Keyboard navigation support for modal and all interactive elements