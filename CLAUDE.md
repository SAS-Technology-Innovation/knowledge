# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the SAS Technology Knowledge Base - a Mintlify documentation site for Singapore American School (SAS).

**Site Purpose:**
Share guides, how-tos, and information about technology, systems, apps, and AI tools used by the SAS community (parents, students, faculty, and staff).

**SAS Branding (implemented):**
- Primary Color: `#1A4190` (SAS Blue)
- Accent Color: `#E51322` (SAS Red)
- Typography: "bebas-neue" for headings, Arial/Helvetica for body
- Tagline: "The Eagle Way"
- Site Name: "SAS Technology Knowledge Base"

## Development Commands

### Local Development
```bash
# Install Mintlify CLI globally (one-time setup)
npm i -g mint

# Start local development server
mint dev

# Development server runs at http://localhost:3000

# Run on custom port
mint dev --port 3333

# Update CLI to latest version
mint update

# Validate links
mint broken-links
```

### Troubleshooting
- If dev environment isn't running: `mint update`
- If page loads as 404: Ensure you're in the directory with `docs.json`
- Node.js version 19+ required

## Architecture

### Configuration System (`docs.json`)

The entire site is configured through a single JSON file at the root. This controls:

**Core Settings:**
- `name`: Site title (now "SAS Technology Knowledge Base")
- `colors`: Theme colors (now SAS blue #1A4190 and red #E51322)
- `logo`: Paths to light/dark mode logos (SAS eagle logos)
- `favicon`: Site favicon path (SAS eagle icon)

**Navigation Structure:**
- Uses a `tabs` array for top-level navigation
- Each tab contains `groups` which organize pages
- Pages reference MDX files by relative path (without `.mdx` extension)
- Example: `"index"` references `index.mdx` in root

**External Links:**
- `navigation.global.anchors`: External links in sidebar
- `navbar.links`: Links in top navbar
- `footer.socials`: Social media links in footer

**Current Structure:**
- Single "Home" tab with landing page
- Ready for expansion with technology guides, apps, AI resources, and systems documentation

### Content Structure

**MDX Files:**
All content is written in MDX (Markdown + React components). Every file must include frontmatter with required `title` and `description` fields (see Frontmatter Requirements section below for details).

**Component Usage:**
Mintlify provides built-in components used throughout:
- `<Card>` - Clickable cards with icons
- `<CardGroup>` - Grid container for cards
- `<Accordion>` / `<AccordionGroup>` - Collapsible sections
- `<Steps>` / `<Step>` - Step-by-step instructions
- `<Note>`, `<Tip>`, `<Warning>`, `<Info>` - Callout boxes
- `<Frame>` - Image containers
- `<Columns>` - Multi-column layouts

### Asset Organization

```
/logo/              - SAS eagle logo files (light.svg, dark.svg) - UPDATED
/images/            - General images and screenshots
/favicon.svg        - SAS eagle favicon - UPDATED
```

**Logo Assets:**
- SAS eagle logos for light and dark modes already in place
- Referenced in `docs.json` with relative paths

### Page Navigation Flow

1. User navigates to a page
2. Mintlify reads `docs.json` to build navigation structure
3. Corresponding MDX file is rendered
4. Components are processed and styled per theme
5. Colors from `docs.json` applied throughout

## Site Organization

**Landing Page (index.mdx):**
The home page organizes content into four main categories:
1. **Technology Guides** - Step-by-step how-tos for SAS systems
2. **Apps & Tools** - Information about SAS applications
3. **AI Resources** - AI tools and responsible usage guides
4. **Systems & Platforms** - SAS technology infrastructure

**Target Audiences:**
- Parents (accessing systems, communication tools, student info)
- Students (learning platforms, collaboration tools, academic apps)
- Faculty & Staff (instructional tech, administrative systems)

**When adding new content:**
- Create folder structure matching the four main categories
- Update `docs.json` navigation to add new pages
- Ensure all pages serve one of the three audiences
- Follow SAS branding and the content strategy below

## Working Relationship

- You can push back on ideas - this can lead to better documentation. Cite sources and explain your reasoning when you do so
- ALWAYS ask for clarification rather than making assumptions
- NEVER lie, guess, or make up information

## Content Strategy

- Document just enough for user success - not too much, not too little
- Prioritize accuracy and usability of information
- Make content evergreen when possible
- Search for existing information before adding new content. Avoid duplication unless it is done for a strategic reason
- Check existing patterns for consistency
- Start by making the smallest reasonable changes
- Focus on practical how-tos for technology, systems, apps, and AI tools
- Write for the SAS community: parents, students, faculty, and staff
- Include "The Eagle Way" ethos when appropriate

## Frontmatter Requirements

Every MDX file must include frontmatter:
- `title`: Clear, descriptive page title (required)
- `description`: Concise summary for SEO/navigation (required)
- `icon`: Font Awesome icon name (optional)

Example:
```mdx
---
title: "Page Title"
description: "Page description"
icon: "gear"
---
```

**Do not skip frontmatter on any MDX file.**

## Writing Standards

- Use second-person voice ("you")
- Include prerequisites at start of procedural content
- Test all code examples before publishing
- Match style and formatting of existing pages
- Include both basic and advanced use cases
- Add language tags on all code blocks
- Include alt text on all images
- Use relative paths for internal links (never absolute URLs for internal links)

## Git Workflow

- NEVER use `--no-verify` when committing
- Ask how to handle uncommitted changes before starting
- Create a new branch when no clear branch exists for changes
- Commit frequently throughout development
- NEVER skip or disable pre-commit hooks

## SEO Configuration

Mintlify automatically handles many SEO best practices (meta tags, sitemap, robots.txt, semantic HTML, mobile optimization). Customize meta tags for Singapore American School as follows:

### Global Meta Tags (in `docs.json`)

Add SAS-specific meta tags in the `seo` section of `docs.json`:

```json
"seo": {
  "metatags": {
    "description": "Singapore American School Knowledge Base - Resources and documentation for the SAS community",
    "keywords": "Singapore American School, SAS, international school, American curriculum, Singapore education",
    "author": "Singapore American School",
    "copyright": "Copyright 2025 Singapore American School",
    "og:title": "SAS Knowledge Base",
    "og:type": "website",
    "og:url": "https://your-sas-docs-domain.com",
    "og:image": "https://your-sas-docs-domain.com/images/sas-social-card.jpg",
    "og:description": "Singapore American School Knowledge Base - The Eagle Way",
    "og:site_name": "SAS Knowledge Base",
    "og:locale": "en_US",
    "twitter:card": "summary_large_image",
    "twitter:site": "@SingAmSchool",
    "twitter:title": "SAS Knowledge Base",
    "twitter:description": "Singapore American School Knowledge Base - The Eagle Way",
    "twitter:image": "https://your-sas-docs-domain.com/images/sas-social-card.jpg",
    "theme-color": "#1A4190",
    "language": "en",
    "distribution": "global",
    "coverage": "Singapore",
    "category": "Education"
  }
}
```

### Page-Specific Meta Tags (in frontmatter)

Override global meta tags for specific pages:

```mdx
---
title: "Parent Resources"
description: "Essential resources and guides for SAS parents"
"og:image": "https://your-domain.com/images/parent-resources.jpg"
---
```

**Note:** Meta tags with colons must be wrapped in quotes.

### SAS Social Media Card Image

The `og:image` should be an SAS-branded image that Mintlify overlays with your logo, page title, and description. Recommended:
- Size: 1200x630px
- Include SAS eagle logo and blue (#1A4190) branding
- Store in `/images/sas-social-card.jpg`

Preview meta tags at [metatags.io](https://metatags.io/)

### Sitemap and Indexing

Mintlify auto-generates `sitemap.xml` and `robots.txt`. To include hidden pages in the sitemap:

```json
"seo": {
  "indexing": "all"
}
```

View sitemap at: `https://your-domain.com/sitemap.xml`

### Disable Indexing (for internal/draft pages)

Add to page frontmatter:
```mdx
---
noindex: true
---
```

Or disable indexing globally in `docs.json`:
```json
"seo": {
  "metatags": {
    "robots": "noindex"
  }
}
```

### SEO Best Practices for SAS Content

**Titles and Descriptions:**
- Use clear, descriptive titles (50-60 characters)
- Write compelling descriptions (150-160 characters)
- Include "SAS" or "Singapore American School" in key pages
- Make each page title and description unique

**Content Structure:**
- Use proper heading hierarchy (H1 → H2 → H3)
- Write for the SAS community (parents, students, teachers) first
- Include relevant keywords: "SAS", "Singapore American School", "Eagle Way"
- Keep URLs short and descriptive
- Break up long content with subheadings and lists

**Internal Linking:**
- Link to related pages within documentation
- Use descriptive anchor text instead of "click here"
- Create topic clusters by linking related concepts
- Use Mintlify's automatic cross-referencing features

**Image SEO:**
- Use descriptive file names (e.g., `sas-campus-library.jpg`)
- Always include alt text for accessibility and SEO
- Optimize image file sizes for faster loading
- Use relevant SAS images that support content

## Deployment

Changes deploy automatically via GitHub integration:
- Install Mintlify GitHub app from dashboard
- Push to default branch (main)
- Site updates automatically

Dashboard: https://dashboard.mintlify.com
