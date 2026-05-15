---
sitemap: false
---
# /assets/images/blog/

Blog post imagery lives here. Conventions:

- **Per-post folder**: `/assets/images/blog/[slug]/hero.jpg` and `og.jpg`
- **Default fallback hero**: `/assets/images/blog/default-electric-fortress.jpg`

## default-electric-fortress.jpg — NEEDS DESIGN

The `blog-post` layout falls back to `default-electric-fortress.jpg` when a post does not declare its own `image:` frontmatter. **This file does not yet exist** and must be created by design.

Spec:

- Dimensions: **1200 x 675** (16:9, also satisfies Open Graph 1.91:1 close enough; if a tighter OG variant is needed, ship `default-electric-fortress-og.jpg` at 1200x630)
- Background: **Deep Slate `#0F172A`**
- Foreground: **Verascribe wordmark in Neon Purple `#A855F7`**
- Style: Electric Fortress palette — cyber-security aesthetic, not wellness. May include subtle teal `#14B8A6` accent line or geometric mark. No gradients heavier than 10 percent.
- Typography on the image (if any): DM Sans
- File format: JPEG, quality ~85, < 200 KB

Until this image exists, posts that do not declare their own hero will render a broken image. Bram has staged the layout fallback path; design ship is the remaining blocker.
