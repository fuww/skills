---
name: brand-guidelines-fashionunited
description: Applies FashionUnited's official brand colors and typography to any sort of artifact that may benefit from having FashionUnited's look-and-feel. Use it when brand colors or style guidelines, visual formatting, or company design standards apply.
license: Complete terms in LICENSE.txt
---

# FashionUnited Brand Styling

## Overview

To access FashionUnited's official brand identity and style resources, use this skill. FashionUnited is a leading B2B fashion platform providing news, jobs, marketplace, and business intelligence for the fashion industry.

**Keywords**: branding, corporate identity, visual identity, post-processing, styling, brand colors, typography, FashionUnited brand, visual formatting, visual design, fashion industry

## Brand Guidelines

### Colors

**Primary Brand Color:**

- Primary: `#ea0151` (rose[600]) - Main brand color for CTAs, links, and brand elements
  - RGB: `rgb(234, 0, 81)`
  - HSL: `hsl(339, 100%, 46%)`
  - OKLCH: `oklch(60% 0.24 14)` (sRGB)
  - OKLCH P3: `oklch(60% 0.27 14)` (enhanced for P3 displays)

**Dashboard Theme Colors:**

- Dashboard Primary: `#ff7a00` (orange) - Dashboard-specific UI elements
- Dashboard Secondary: `#376d99` (blue) - Secondary dashboard actions
- Success: `#679937` (green) - Confirmations and positive states
- Error: `#ff0000` (red) - Error messages and warnings
- Scheduled: `#fad201` (yellow) - Pending and scheduled states

**Text Colors:**

- High Emphasis: `rgba(0, 0, 0, 0.87)` - Primary text
- Medium Emphasis: `rgba(0, 0, 0, 0.6)` - Secondary text
- Inactive: `rgba(0, 0, 0, 0.54)` - Inactive elements
- Disabled: `rgba(0, 0, 0, 0.38)` - Disabled elements

**Neutral Colors:**

- Black: `#000000`
- Grey Dark: `#58595b` - Secondary text and borders
- Grey Light: `#dbdbdb` - Subtle backgrounds and dividers
- White: `#ffffff`
- White Light: `rgba(255, 255, 255, 0.7)` - Subtle overlays

**Rose Color Scale:**

- rose[50]: `#fff1f2` - Lightest tint
- rose[100]: `#ffe9ea`
- rose[200]: `#ffd5d9`
- rose[300]: `#ffb1bc`
- rose[400]: `#ff7f98`
- rose[500]: `#ff2468`
- rose[600]: `#ea0151` - Primary brand color
- rose[700]: `#d30045`
- rose[800]: `#b40036`
- rose[900]: `#a2002f`
- rose[950]: `#5d0918` - Darkest shade

### Typography

- **Primary Font**: Helvetica Neue, Helvetica, -apple-system, BlinkMacSystemFont, Roboto, Arial, sans-serif
- **Secondary Font**: Helvetica Neue, Helvetica, -apple-system, BlinkMacSystemFont, Roboto, Arial, sans-serif
- **Article Font**: Georgia, Cambria, "Bitstream Charter", "Charis SIL", Utopia, serif (for long-form content)
- **System Font**: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif
- **Note**: Fonts use system fonts for optimal performance and consistency

## Features

### Smart Font Application

- Applies Helvetica Neue/system fonts to all text elements
- Uses Georgia and serif fonts for article content
- Automatically falls back to system fonts if unavailable
- Preserves readability and consistency across all platforms

### Text Styling

- Primary text: Helvetica Neue, Helvetica, or system sans-serif
- Article content: Georgia, Cambria, or serif fonts
- Smart color selection based on emphasis level
- Follows Material Design text hierarchy patterns
- Preserves text hierarchy and formatting

### Brand Color System

- Primary brand color (rose #ea0151) for main actions and links
- Dashboard-specific orange (#ff7a00) for admin interfaces
- Semantic colors (success green, error red, warning yellow)
- Complete rose color scale (50-950) for gradients and variations
- Text colors follow Material Design opacity guidelines

### Color Usage Guidelines

- **Main Application**: Use rose[600] #ea0151 for primary buttons, CTAs, and brand elements
- **Dashboard Theme**: Use orange #ff7a00 for dashboard-specific UI
- **Semantic Colors**: Apply green for success, red for errors, yellow for warnings
- **Text Hierarchy**: Use opacity-based text colors for emphasis levels
- **P3 Display Support**: Enhanced colors for modern displays with wide color gamut

## Technical Details

### Font Management

- Uses system fonts (Helvetica Neue, -apple-system, BlinkMacSystemFont, Roboto)
- No custom font installation required
- Optimized for web and application performance
- Provides consistent rendering across different platforms
- Special serif stack for article/editorial content

### Color Application

- Primary uses RGB, HSL, and OKLCH color specifications
- P3 display support for enhanced color on modern screens
- RGBA values for text with proper opacity levels
- Complete rose color scale for brand consistency
- Maintains color fidelity across different systems and displays

### Spacing and Layout

- Base spacing unit: 8px
- Mobile-first responsive approach
- Component spacing: 16px (mobile), 20px (tablet), 24px (desktop)
- Follows Material Design spacing guidelines

### Typography Scale

FashionUnited uses a comprehensive type scale with specific sizing and spacing:

| Style | Font Size | Line Height | Letter Spacing | Font Weight |
|-------|-----------|-------------|----------------|-------------|
| **Headline 1** | 3rem (48px) | 3rem (48px) | -0.104rem | Bold |
| **Headline 2** | 2.25rem (36px) | 2.5rem (40px) | -0.097rem | Bold |
| **Headline 3** | 1.875rem (30px) | 2.25rem (36px) | -0.030rem | Bold |
| **Headline 4** | 1.5rem (24px) | 2rem (32px) | -0.042rem | Bold |
| **Headline 5** | 1.25rem (20px) | 1.75rem (28px) | 0 | Bold |
| **Headline 6** | 1.125rem (18px) | 1.75rem (28px) | 0 | Bold |
| **Subtitle 1** | 0.875rem (14px) | 1.5rem (24px) | 0.011rem | Bold |
| **Subtitle 2** | 0.75rem (12px) | 1.25rem (20px) | 0.008rem | Bold |
| **Body 1** | 1rem (16px) | 1.5rem (24px) | 0 | Normal |
| **Body 2** | 0.875rem (14px) | 1.25rem (20px) | 0 | Normal |
| **Button** | 0.875rem (14px) | 1.25rem (20px) | 0 | Bold, Uppercase |
| **Caption** | 0.75rem (12px) | 1rem (16px) | 0.033rem | Bold |
| **Overline** | 0.625rem (10px) | 0.875rem (14px) | 0.150rem | Bold, Uppercase |

### Responsive Breakpoints

| Breakpoint | Min Width | Description |
|------------|-----------|-------------|
| **xs** | 0px | Extra small devices (mobile) |
| **xssm** | 480px | Small mobile (custom breakpoint) |
| **sm** | 600px | Small tablets (portrait) |
| **md** | 840px | Tablets (landscape) |
| **lg** | 1024px | Desktop (standard) |
| **xl** | 1920px | Large desktop (wide screens) |

### Design Resources

- **Figma Components**: Full component library available in Figma
- **Storybook**: Live component documentation at fashionunited.com/storybook/
- **Material Icons**: Standard icon library
- **Corporate Identity**: Logo and brand assets in Google Drive
