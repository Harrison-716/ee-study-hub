# AGENTS.md — EE Study Hub

## 1. Mission
EE Study Hub is a Traditional Chinese, beginner-friendly electrical engineering study library. Its goal is to turn course concepts into concise, accurate, searchable notes. Every future contribution must preserve a consistent layout and a repeatable content workflow.

## 2. Technology and constraints
- Static site only: HTML5, CSS3 and vanilla JavaScript (ES modules). No build tools, frameworks, accounts, server or external API.
- Deploy from the repository root with GitHub Pages. Use relative URLs so the site also works at `/repository-name/`.
- Use semantic HTML, responsive layouts, keyboard-accessible controls and visible focus states.
- All user-facing copy is in Traditional Chinese. Technical symbols and standard English terms may remain in English.
- Never insert user secrets, credentials, personal identifiers or copied textbook passages.

## 3. Directory map
```
index.html                 # Landing page and note browser
assets/styles.css          # Design tokens, components and responsive styling
assets/app.js              # Rendering, filters, theme and navigation
content/notes.js           # Single source of truth for note metadata and content
AGENTS.md                  # Rules for AI contributors
README.md                  # Setup, usage and deployment
```
Do not add files outside these locations without explaining the reason in README.md.

## 4. Visual design system
- Clean academic dashboard; primary blue `#4f70e8`, dark navy surfaces and soft neutral backgrounds.
- Use system fonts, 8px spacing rhythm, rounded cards, subtle borders and generous whitespace.
- Use CSS variables for colors, spacing and radii. Support light and dark themes.
- Keep a consistent hierarchy: site header > section title > note title > subheading > body.
- At widths below 760px, stack the hero and cards; avoid horizontal overflow.

## 5. Note data contract
Every note is an object in the exported `notes` array in `content/notes.js` with EXACTLY these fields:
- `id`: unique lowercase kebab-case ASCII slug, e.g. `diode-basics`.
- `course`: one of `電子學`, `電路學`, `線性代數`, `程式設計`.
- `title`: concise Traditional Chinese title.
- `level`: one of `入門`, `進階`.
- `summary`: one-sentence description, maximum 80 Chinese characters.
- `updated`: ISO date `YYYY-MM-DD`.
- `sections`: nonempty array of objects, each containing `heading` and `body` as plain text strings.
Each note should include at least three sections: `核心觀念`, `重要公式／方法`, and `常見錯誤` (additional sections allowed). Write mathematical expressions as plain Unicode text; do not inject HTML into note content.

## 6. How AI must add a note
1. Read AGENTS.md and inspect the existing `notes` array and UI before editing.
2. Confirm the topic belongs to one of the supported courses; otherwise propose a new course and update filters and documentation together.
3. Create an original explanation; verify technical accuracy and clearly label simplifications or assumptions.
4. Add one note object following the exact schema; check slug uniqueness and date format.
5. Keep each section short and actionable. Include one common misconception or pitfall.
6. Do not alter existing note IDs, break deep links or change the UI structure unnecessarily.
7. Test the new note via course filter, search, card click, URL hash, back navigation, mobile layout and both themes.
8. Update README.md if functionality or project structure changes.

## 7. How AI must modify UI or behavior
- Prefer small, scoped edits. Reuse existing classes, CSS variables and rendering helpers.
- Never use `innerHTML` with untrusted content; use `textContent` for notes.
- Maintain keyboard usability, contrast, descriptive button labels and reduced-motion support.
- Preserve the URL format `#note/<id>` for individual notes and `#home` for the overview.
- Search must match title, course, summary and section text; course filters must combine with search.
- Do not introduce dependencies without explicit approval.

## 8. Acceptance checklist
- [ ] Site loads without errors on GitHub Pages and locally.
- [ ] At least one note per course; no duplicate IDs.
- [ ] Search, course filters, note details, deep links and back navigation work.
- [ ] Mobile and desktop layouts work; light/dark theme persists.
- [ ] No broken relative paths or secrets.
- [ ] New content follows the schema and the site's visual language.

## 9. Example instruction for future AI
> 請先閱讀 AGENTS.md，再為「電子學」新增一篇「BJT 工作區域判斷」筆記。依照 notes.js 的欄位格式撰寫核心觀念、重要公式／方法及常見錯誤，檢查搜尋、分類和詳細頁是否正常，除必要修改外不要更動既有版面。
