# Publish: Put a finished piece on the site

Take a finalized essay or note and publish it to maninae.github.io.

## Input

`$ARGUMENTS` can be:
- A title or slug for a piece drafted in this conversation or a previous `/draft` session
- If no arguments, look for the most recently drafted piece in the conversation

The user should have a finalized piece ready (title, body, type, tags). If not, suggest running `/draft` first.

## Required metadata

Before publishing, confirm with the user:
- **Title**: The piece title
- **Type**: essay or note
- **Tags**: Freeform tags (e.g., "craft", "ml", "observations")
- **Date**: Default to today's date
- **Lead**: The hook/opening line that appears in the listing (Steph Ango style)

## Publishing steps

1. **Generate the slug** from the title (lowercase, hyphens, no special chars).
   Example: "On Building Things That Last" → `on-building-things-that-last`

2. **Create the article HTML file** at `writing/{slug}.html`:
   - Read `writing/_template.html` for the base structure (BUT update it to use the current design system if it still has old Tailwind/Figtree styles)
   - Use the shared nav (Writing marked active), footer, fonts (Cormorant Garamond + DM Sans), and link to `../styles.css`
   - Include dark mode toggle and theme script
   - Article header: title in Cormorant Garamond, date below, tags as pills
   - Article body: the content with proper `.article-body` typography
   - Back link: "← Back to Writing"

3. **Update `writing.html`** — add the new piece to the listing:
   - Essays go in the essays section, notes in the notes section
   - Include: date, tags, title, lead/hook line
   - Link to `writing/{slug}.html`
   - Keep listings in reverse chronological order (newest first)

4. **Update `index.html`** homepage if needed:
   - If the piece is one of the 3 most recent essays, update the essays column
   - If the piece is one of the 5 most recent notes, update the notes column
   - Maintain the Steph Ango style: title + italic lead + "keep reading →"

5. **Show the user a summary** of all files changed and ask to confirm before committing.

6. **Commit** with message: "Publish {type}: {title}"

## Article HTML structure

The article page should have:
- `<title>{Title} — Owen Wang</title>`
- `<meta name="description" content="{lead text}">`
- Nav with Writing active + dark mode toggle
- Back to Writing link
- Article header (title, date, tag pills)
- Article body with editorial typography (serif headings, generous line-height)
- Footer with social links

## Template update note

The existing `writing/_template.html` uses the OLD design (Tailwind, Figtree, teal colors). On first run, update it to match the current design system (pure CSS, Cormorant Garamond + DM Sans, Pale Parchment palette, dark mode support). Then use it as the base for all future articles.
