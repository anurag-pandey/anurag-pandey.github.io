# Website Improvement Roadmap

This file tracks improvements for anuragpandey.net. Each task is self-contained and can be picked up independently.
Status: `[ ]` = todo, `[x]` = done, `[-]` = skipped

---

## Tier 1: Quick Wins (one-time setup, high impact)

### Task 1.1: Add site description for SEO
- **File:** `_config.yml`
- **What:** Add a meaningful `description` value (currently blank). This shows up in Google search results, social media previews (via jekyll-seo-tag), and RSS feed metadata.
- **Example:** `description: "Anurag Pandey's personal site — writing about startups, engineering, investing, and building things."`
- **Status:** `[x]` (Done — set to "Anurag Pandey's personal blog")

### Task 1.2: Add jekyll-sitemap plugin
- **File:** `_config.yml`, `Gemfile`
- **What:** Add `jekyll-sitemap` to plugins list in `_config.yml` and `Gemfile`. This auto-generates a `sitemap.xml` that search engines use to discover all pages.
- **Steps:**
  1. Add `gem "jekyll-sitemap"` to `Gemfile`
  2. Add `- jekyll-sitemap` to the `plugins:` list in `_config.yml`
  3. Run `bundle install`
  4. Verify sitemap generates at `/sitemap.xml` with `bundle exec jekyll build`
- **Note:** GitHub Pages natively supports jekyll-sitemap, so it will work without any extra config once deployed.
- **Status:** `[x]` (Done)

### Task 1.3: Enable analytics (privacy-friendly)
- **File:** `_includes/head.html`
- **What:** The site has a Google Analytics hook in `head.html` but it's not configured. Instead of Google Analytics, consider adding GoatCounter (free, privacy-friendly, no cookie banner needed).
- **Steps:**
  1. Sign up at https://www.goatcounter.com (free for personal use)
  2. Add the GoatCounter script tag to `_includes/head.html`
  3. Remove or leave the unused Google Analytics conditional
- **Alternative:** If you prefer Google Analytics, just add `google_analytics: "G-XXXXXXXXXX"` to `_config.yml` — the existing template code will activate.
- **Status:** `[ ]`

### Task 1.4: Fix the empty "rock" blog post
- **File:** `_posts/2025-04-10-rock.md`
- **What:** This post has a title but no body content. Either add content or remove it — empty posts look unfinished.
- **Status:** `[ ]`

### Task 1.5: Submit site to Google Search Console
- **What:** This is a manual step (not code). Go to https://search.google.com/search-console, add `anuragpandey.net`, verify ownership via DNS, and submit the sitemap URL (after Task 1.2 is done).
- **Status:** `[ ]`

---

## Tier 2: Professional Brand

### Task 2.1: Create a dedicated About page
- **File:** Create `about.md` in root
- **What:** A proper about page with your story, career journey (chemical engineering -> gaming/tech), what you're working on now, and what you care about. The homepage intro is too brief to serve as a real "about" page.
- **Layout:** Use `layout: page` with `title: About` and `permalink: /about/`
- **Sections to include:** Who you are, what you do, what you've built, how to reach you.
- **Status:** `[ ]`

### Task 2.2: Create a Projects page
- **Files:** Create `_data/projects.yml` and `projects.html` in root
- **What:** A page listing things you've worked on. Use a Jekyll data file (`_data/projects.yml`) so adding new projects is just adding YAML entries.
- **Data file format:**
  ```yaml
  - name: "Project Name"
    description: "One-line description"
    url: "https://..."
    tags: ["gaming", "startup"]
    year: 2024
  ```
- **Template:** Loop through `site.data.projects` and render cards (similar style to your blog cards).
- **Status:** `[ ]`

### Task 2.3: Create a /now page
- **File:** Create `now.md` in root
- **What:** A page describing what you're currently focused on. Updated monthly. See https://nownownow.com for the concept. Use `layout: page`, `title: Now`, `permalink: /now/`.
- **Content ideas:** Current role, what you're reading, what you're learning, what you're building.
- **Status:** `[ ]`

### Task 2.4: Add navigation links for new pages
- **File:** `_config.yml` or relevant layout/include files
- **What:** After creating About, Projects, and Now pages, make sure they appear in the site header navigation. Minima auto-adds pages with `title` in frontmatter to the nav, so this may happen automatically — verify and adjust order if needed.
- **Status:** `[ ]`

---

## Tier 3: Digital Garden / Second Brain

### Task 3.1: Create a TIL (Today I Learned) collection
- **Files:** `_config.yml`, create `_til/` directory, create `til.html` page
- **What:** A collection of short posts (3-5 sentences each) about things you learn. Low friction writing — no pressure for polished essays.
- **Steps:**
  1. Add to `_config.yml`:
     ```yaml
     collections:
       til:
         output: true
         permalink: /til/:title/
     ```
  2. Create `_til/` directory
  3. Create `til.html` listing page with `permalink: /til/`
  4. Add a sample TIL entry in `_til/` to test
- **Status:** `[ ]`

### Task 3.2: Create a Bookshelf / Reading page
- **Files:** Create `_data/books.yml` and `bookshelf.html` in root
- **What:** A list of books you've read with one-line takeaways. Maintained via a simple YAML data file.
- **Data file format:**
  ```yaml
  - title: "Book Title"
    author: "Author Name"
    takeaway: "One line on what you got from it"
    year_read: 2024
    rating: 5  # optional, out of 5
  ```
- **Status:** `[ ]`

### Task 3.3: Create a Links / Bookmarks page
- **Files:** Create `_data/links.yml` and `links.html` in root
- **What:** Curated links organized by topic (startups, engineering, investing, etc.). A "best of the internet" resource page.
- **Data file format:**
  ```yaml
  - category: "Startups"
    links:
      - title: "Paul Graham - Do Things That Don't Scale"
        url: "http://paulgraham.com/ds.html"
        note: "The classic essay on early-stage startup tactics"
  ```
- **Status:** `[ ]`

---

## Tier 4: Audience Building

### Task 4.1: Add email subscription via Buttondown
- **What:** Buttondown (https://buttondown.com) is free for up to 100 subscribers. It can pull from your RSS feed. Add a subscribe link/section to your blog page or footer.
- **Steps:**
  1. Sign up at Buttondown and configure your RSS feed URL
  2. Add a "Subscribe" link in the footer (`_includes/footer.html`) or on `blog.md`
  3. Style it to match the site's dark theme
- **Status:** `[ ]`

### Task 4.2: Add canonical URL support for cross-posting
- **File:** `_includes/head.html`
- **What:** When you cross-post articles to DEV.to or Hashnode, you need a canonical URL pointing back to your site. jekyll-seo-tag already handles this, but verify it's outputting `<link rel="canonical">` tags correctly.
- **Status:** `[ ]`

### Task 4.3: Add Open Graph / Twitter Card meta tags
- **File:** `_includes/head.html`
- **What:** Ensure that when your posts are shared on social media, they show rich previews (title, description, image). jekyll-seo-tag handles basics, but verify OG tags are rendering. Consider adding a default social sharing image in `/assets/images/`.
- **Status:** `[ ]`

---

## Housekeeping

### Task H.1: Exclude internal files from Jekyll build
- **File:** `_config.yml`
- **What:** CLAUDE.md, TASKS.md, and README.md should not appear on the live website. Add them to the `exclude:` list in `_config.yml`.
- **Status:** `[x]` (Done)

### Task H.3: Fix Ruby environment and gem vulnerabilities
- **What:** The local Ruby setup is outdated and has known vulnerabilities. Fix all of the following:
  1. **Ruby version:** Currently on 2.6.10 (EOL). Upgrade to Ruby 3.x via `rbenv` or `ruby-install`.
  2. **RubyGems version:** Currently 3.0.3.1 with a known `required_ruby_version` bug. Upgrade via `gem update --system`.
  3. **Dependabot alert #9 (high):** `google-protobuf` has a potential Denial of Service vulnerability. Update the gem or its parent dependency.
  4. **Sass deprecation warnings:** Minima theme uses `/` for division (deprecated in Dart Sass 2.0). Investigate if a Minima version bump fixes this.
  5. Run `bundle audit` (install `bundler-audit` gem first) to check for any additional vulnerabilities and fix them.
- **Goal:** Zero known vulnerabilities, no deprecation warnings, modern Ruby version.
- **Status:** `[x]` (Done — Ruby upgraded to 3.3.11 via rbenv, all gems updated, google-protobuf vuln fixed, SCSS compiled to plain CSS eliminating all Sass deprecation warnings, bundler-audit reports zero vulnerabilities)

### Task H.2: Clean up _config.yml
- **File:** `_config.yml`
- **What:** Uncomment and fill in `twitter_username` and `github_username` if you want social links in the default Minima footer/head. Remove them entirely if you don't use those platforms.
- **Status:** `[x]` (Done — set description, url, author; uncommented social usernames; removed custom footer and Font Awesome CDN import in favor of Minima defaults)

---

## How to use this file with Claude Code

When working in Claude Code terminal, you can say things like:
- "Pick up Task 1.2 from TASKS.md" — Claude Code will read this file and implement that specific task
- "What's the next pending task?" — Claude Code will scan for `[ ]` items
- "Mark Task 1.1 as done" — Claude Code will update the status
- "Implement all Tier 1 tasks" — Claude Code will work through them sequentially

Each task is designed to be a small, focused change (one commit each).
