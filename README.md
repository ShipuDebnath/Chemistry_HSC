মাস্টার প্রম্পট: যেকোনো অধ্যায়ের ইন্টারঅ্যাকটিভ স্টাডি অ্যাপ
Oct 23, 2026 · @Shipu Debnath
ব্যবহারের নিয়ম
শুধু নিচের "Inputs" অংশে তোমার অধ্যায়ের নাম ও উপ-অংশের তালিকা বসাও, তারপর "Inputs" থেকে শেষ পর্যন্ত পুরো লেখা কপি করে নতুন চ্যাটে দাও। অধ্যায় ২-এর অ্যাপের মতোই একটি অ্যাপ তৈরি হবে — একই পাতা, কুইজ, মেগা টেস্ট, থিম ও সিমুলেশনসহ, কিন্তু তোমার অধ্যায়ের বিষয়বস্তু দিয়ে।
• কী বদলাবে: বিষয়, পত্র, অধ্যায় নম্বর, অধ্যায়ের নাম আর সিলেবাসের উপ-অংশগুলো (বইয়ের নম্বরসহ, যেমন ৩.১, ৩.১.১ …)। বাকি সব যেমন আছে রাখো।
• আউটপুট মোড: standalone = একটি আলাদা পূর্ণ অ্যাপ ফাইল; chapter-block = শুধু একটি অধ্যায়-ব্লক, যা hsc-chemistry.html ফাইলের শেষের "নতুন অধ্যায় এই লাইনের নিচে" চিহ্নের নিচে বসবে (তখন সেই ফাইলটিও চ্যাটে সংযুক্ত করো)।
• একবারে পুরো অ্যাপ আসবে না: কাজ ধাপে ধাপে হবে। প্রতি ধাপের শেষে চেকলিস্ট দেখাবে; "continue" লিখলে পরের ধাপ।
• বিষয় রসায়ন না হলেও (পদার্থবিজ্ঞান, জীববিজ্ঞান, গণিত …) একই প্রম্পট কাজ করবে; চিত্র ও সিমুলেশন বিষয় অনুযায়ী বাছাই হবে।
Inputs (fill these in)
SUBJECT        : রসায়ন                      (e.g. রসায়ন / পদার্থবিজ্ঞান / জীববিজ্ঞান / উচ্চতর গণিত)
LEVEL          : HSC (NCTB, Bangladesh)
PAPER          : ১ম পত্র                     (১ম পত্র / ২য় পত্র)
CHAPTER NO     : [অধ্যায় নম্বর]
CHAPTER NAME   : [অধ্যায়ের নাম]
SUBTOPICS      : (one per line, numbered exactly as in the textbook; unnumbered sub-items allowed)
  [৩.১ …]
  [৩.১.১ …]
  [৩.২ …]
  …
  অধ্যায়ের সারসংক্ষেপ
  অনুশীলনী
LANGUAGE       : Bengali (all UI and content)
OUTPUT MODE    : standalone                (standalone | chapter-block)
Treat the SUBTOPICS list as the complete syllabus: every line must become a section or a lesson with exactly that number and title, in that order, and nothing outside it may be added except the summary and exercise sections.
Role, goal and principles
You are a senior front-end engineer and an experienced HSC teacher of SUBJECT (NCTB, Bangladesh). Build a complete interactive study app for CHAPTER NO · CHAPTER NAME that covers every item in SUBTOPICS, so a student can learn, practise and revise the whole chapter from it alone.
• One self-contained HTML file: plain HTML, CSS and JavaScript, no frameworks, no images or external scripts. The only external request allowed is Google Fonts (Anek Bangla 300–700, Tiro Bangla, JetBrains Mono), and the app must still look right offline with Bengali system-font fallbacks.
• Mobile first: design and test at 390 × 844 px; nothing may scroll sideways on any screen, lesson or visual. Respect safe-area insets. On wide screens (≥ 1080 px) show a sticky sidebar contents list.
• Bengali throughout: every UI label and all content in Bengali, numbers in Bengali digits; formulas, symbols and units stay in Latin script.
• Works offline and remembers everything: progress, notes, highlights, bookmarks, quiz results and theme save automatically in localStorage on every action; if the host page offers account storage (window.claude.use('db') with use('user')), also sync there and merge safely. The app must keep working if storage fails.
• Exam-focused and accurate: content follows the NCTB textbook and board-exam patterns (MCQ, সৃজনশীল/CQ, short and written questions); no padding, no invented facts; where textbooks disagree, say so.
• Accessible: labelled icon buttons, visible focus ring, reduced-motion support, a print style that hides controls and expands all sections.
• Extendable: the code is organised as core (styles, a chapter registry, a visual toolkit, the app engine) plus one clearly marked block per chapter, and the engine starts on DOMContentLoaded, so further chapters can be pasted at the end of the file later. End the file with a commented "add new chapters here" template.
App structure: screens and features
Navigation: a top bar (back, contents menu, chapter title, search, theme) and a bottom bar with five tabs — হোম · পাঠসূচি · অনুশীলন · টুলস · অগ্রগতি. Back button and browser back work through an in-app history stack. Reopening the app resumes the last lesson at the same scroll position, with a toast offering to go Home.
1. Home — greeting and date; "continue where you stopped" card; overall progress card; today's streak, lesson goal and reading-minutes goal; the chapter's sections as a grid of element-style tiles (number, symbol, short title, mastery %, completion bar, coloured by topic group) with a legend; shortcuts to the tools.
2. Contents — every section and lesson in syllabus order with reading time, bookmark/note marks and completion ticks; a slide-in drawer shows the same list from any screen.
3. Section page — title with importance stars, intro, 8 stats (lessons, done, left, completion %, mastery %, quiz score and best, minutes left, days practised in the last 7), lesson list, practice buttons (adaptive quiz, question bank, written practice, flashcards, quiz by difficulty), exam analysis (past question patterns, board-question notes), and the section's formulas.
4. Lesson page — lesson number and title, reading time, bookmark button, the 12 content blocks as collapsible cards (§Content), the lesson's visuals inside the first block, a lesson exercise (all MCQs for this lesson with instant feedback and live score, plus short questions with reveal buttons, and a "try again" reset), an autosaving personal note, a "mark as complete" button (toast + daily-goal message), a quiz prompt after the last lesson of a section, and previous/next lesson buttons. Selecting text offers a highlight button; highlights persist.
5. Question bank (per section) — tabs with counts: MCQ (filter by difficulty), সংক্ষিপ্ত, সৃজনশীল (stimulus + ক খ গ ঘ with marks 1–4 and model answers), বোর্ড ধাঁচ, প্রয়োগমূলক, বিশ্লেষণধর্মী, HOTS, লিখিত অনুশীলন (2, 3, 5, 7, 10-mark questions with model answer, mark distribution and examiner's note).
6. MCQ behaviour everywhere — one tap locks the answer, marks right/wrong, shows the explanation, and on a wrong answer names the lesson the idea comes from with a link to it. Every answer is recorded; wrongly answered questions go to a "wrong questions" list until answered correctly.
7. Adaptive quiz — 10 questions from a section (or from the wrong list); starts at medium, moves one level up after a correct answer and down after a wrong one; progress segments and a timer; report with score ring, verdict, accuracy by difficulty, lessons to revise, and all answers with explanations.
8. Practice hub — entry to the mega test, the wrong-questions quiz, and every section's quiz and bank with last/best score and mastery.
9. Chapter mega test — five parts taken in any order and resumable: A 100 MCQ (auto-marked, question palette, timer), B 50 short questions, C 20 CQ, D 10 analytical, E 5 HOTS sets of 3 (B–E self-marked against model answers). Questions are sampled round-robin across sections. Report: chapter mastery (weighted 40/15/25/10/10), a learning-quality score (mastery, lessons done, consistency over 14 days, accuracy on hard items), per-part scores, weakest sections, and a day-by-day revision plan.
10. Tools — formula sheet (searchable), comparison tables (every difference table in the chapter, grouped and searchable, each linking back to its lesson), flashcards (deck per section or all, flip card, "know it / see again", known count), revision mode (each lesson's short notes, key facts and memory tricks on one page), search across lessons, questions and formulas (opens the lesson at the matched words), library (bookmarks, notes, highlights, wrong questions), and settings.
11. Progress — completion ring, average mastery, MCQ accuracy, time left, streak, active days, total minutes and questions, a 28-day activity heat map, adjustable daily goals, and a card per section with all its numbers.
12. Settings — theme picker, storage/offline explanation, a table of loaded chapters with counts and any structural problems found, and a two-tap "reset all progress".
Mastery of a section = 30% lessons completed + 70% (MCQ accuracy × coverage), where coverage = questions attempted / (60% of the section's questions), capped at 1. An active day = at least one lesson, 3 questions or 5 minutes.
Look and feel: layout, typography, themes
Design concept. Calm and bookish, like a well-kept lab notebook: a warm paper background, white cards, one strong accent colour and one secondary accent. Pick a visual idea that belongs to SUBJECT and use it consistently — for chemistry, show the sections on Home as periodic-table tiles; for physics, as instrument dials; for biology, as specimen cards. Write the chosen idea in a one-line comment at the top of the CSS.
Tokens. Define everything as CSS custom properties on :root and use only the tokens in components: --bg, --surface, --surface-2, --surface-3, --fg, --muted, --line, --line-strong, --accent, --accent-soft, --accent-ink, --accent-2, --accent-2-soft, --ok/--bad/--warn (each with a -soft version), --hl for highlights, --cat-a … --cat-e for the five topic groups, --spec-bg/--spec-fg for dark diagram panels, --shadow, --radius 14px, --radius-sm 9px, --top-h 56px, --nav-h 62px.
Typography. Headings in Tiro Bangla (serif), body in Anek Bangla, formulas and numbers in JetBrains Mono. Body 16.5px with line-height about 1.75 for Bengali; lesson column max about 720px wide. Superscripts and subscripts must be real <sup>/<sub>, never written as plain characters.
Components. 44px minimum touch targets; cards with 1px border and soft shadow; collapsible lesson blocks with an icon chip coloured by block type; chips and pills for counts; segmented tabs that scroll sideways inside themselves when they overflow; tables inside a .table-wrap that scrolls sideways on its own; toasts above the bottom bar; bottom sheets for menus and the chapter picker; a progress ring and bar component; skeleton-free instant rendering. One set of thin line icons (24-unit viewBox, 1.8 stroke, round caps) drawn inline as SVG.
Themes (picker in the top bar and in Settings, remembered; "auto" follows the device light/dark setting):
Theme
Feel
Background · accent
Vanilla (default)
warm paper
#F7F3EA · #1F4E8C
Ocean
cool, clean
#EDF5F7 · #0B6E8A
Glass
frosted iOS-style cards over a soft colour wallpaper (backdrop blur, translucent surfaces, white hairline borders)
#E9ECFA · #0071E3
Sakura
soft pink
#FBF0F3 · #B0275A
Matcha
soft green
#EDF1E4 · #3D6B21
High contrast
black on white, thick borders, for low vision
#FFFFFF · #0033CC
Dark
near-black, low glare
#0E0F13 · #8DB6FF
Every theme sets all tokens, keeps text contrast at WCAG AA or better, and must look right on every screen and inside every visual — visuals take their colours from the tokens, so they switch with the theme automatically. Apply the theme with a data-skin attribute on <html> and set the browser theme-color meta to match.
Motion. Short (150–250 ms) fades and slides for screen changes, sheets and card expansion; nothing moves when the device asks for reduced motion.
Content for every subtopic
From SUBTOPICS to sections and lessons
• Each top-level number in SUBTOPICS (X.1, X.2 …) becomes a section; each sub-number under it (X.1.1, X.1.2 …) becomes a lesson in that section. A top-level item with no sub-items becomes a section with one lesson of the same number and title. Keep the textbook numbers and titles exactly.
• Group the sections into four topic groups A–D (name them in the chapter declaration); group E is for "অধ্যায়ের সারসংক্ষেপ" and "অনুশীলনী".
• Give every section a 1–2 letter tile symbol, a short title for the tile, and an exam importance from 1 to 5 based on how often boards ask it.
• Prefix every id with the chapter id (for chapter 5: c5, c5s3, c5s3b, c5_titration) so several chapters can live in one file.
Data shape (one object per section)
HSC.chapter({ id, paper, no, order, t, en, desc, cats:{A,B,C,D,E} })
SEC.push({
  id, no, sym, cat, w, t, st, intro,
  exam: { pat:[past-question patterns], board:[board-question analysis] },
  L: [ { id, no, t, v:[visual ids],
         ov, dp, sc,                      // HTML strings
         fx, ap, cm, tr, sn, mh, mf, cf,  // arrays of strings
         ho:[[question, answer]],
         xm:[[q, [4 options], answerIndex 0-3, 'e'|'m'|'h', explanation]],
         xs:[[question, answer]] } ],
  Q: { mcq:[[q,[4 options],answerIndex,diff,explanation,lessonId]],
       sq, bq, aq, nq, hq:[[question, answer]],
       cq:[{ s: stimulus, p:[[ক q, a],[খ q, a],[গ q, a],[ঘ q, a]] }],
       wp:[[marks, question, model answer, mark distribution, examiner note]] },
  F:[[front, back]],  FM:[[name, formula, note]]
})
VIS.<id> = { t, k, cap, html(), mount(el) }
CMPT.push({ g: group, t: title, l: lessonId, k: heading before the table })
The app validates this on load (unique ids, every lesson visual exists, answer index 0–3, four options, lesson ids valid) and lists any problem in Settings.
The 12 blocks of every lesson
Key
Heading shown
What goes in it
Size
ov
সহজ ভাষায় ধারণা
the idea in plain words with an everyday analogy; the lesson's visual sits here
50–80 words
dp
বিস্তারিত ব্যাখ্যা
the full textbook treatment with <h4> sub-headings: definitions, explanation, worked examples, tables, equations; for a practical: aim, principle, apparatus, procedure, observation table, conclusion, precautions
about 300 words, more for practicals
sc
বৈজ্ঞানিক বিশ্লেষণ
formulas, derivation, the maths, limits and exceptions
about 120 words
fx
গুরুত্বপূর্ণ তথ্য
crisp exam facts and values
4–6 items
ap
বাস্তব জীবনে প্রয়োগ
uses in daily life, industry, medicine, Bangladesh context
3–4
cm
সাধারণ ভুল
mistakes students really make, each with the correction
3–4
tr
পরীক্ষার কৌশল
how this is asked and how to score full marks
3
sn
সংক্ষিপ্ত নোট
one-line revision notes
4–6
mh
মনে রাখার কৌশল
mnemonics, patterns, tricks in Bengali
1–3
mf
MCQ ফোকাস পয়েন্ট
the facts MCQs test most
3–5
cf
CQ ফোকাস পয়েন্ট
what গ and ঘ parts usually demand
2–4
ho
উচ্চতর চিন্তন দক্ষতা (HOTS)
why/what-if questions with full answers
1–2
Then the lesson exercise: xm 10–20 MCQs that together test every fact, value and idea in the lesson (more for long lessons), and xs 6–10 short questions with answers.
Question bank per section
• mcq 10–15 extra MCQs that mix the section's lessons (each tagged with its lesson id); the bank shows these plus all lesson MCQs.
• sq 6–10 short questions; cq at least 2 creative questions (3 for weight 4–5 sections); bq 3–5 board-style; aq 3–5 application; nq 3–5 analytical; hq 2–3 HOTS.
• wp exactly 5 written questions worth 2, 3, 5, 7 and 10 marks, each with model answer, mark distribution and an examiner's note.
• F 8–14 flashcards; FM every formula, constant or reaction pattern in the section (can be empty only if there truly are none); exam 3–5 past patterns and 3–5 board analysis notes.
• Chapter totals must at least feed the mega test: 100 MCQ, 50 short, 20 CQ, 10 analytical and 15 HOTS questions.
Summary and exercise sections (group E)
• অধ্যায়ের সারসংক্ষেপ: a concept map of the whole chapter, every key definition, all formulas, all comparisons in one place, the top mistakes, and a one-page last-night revision list.
• অনুশীলনী: textbook-style exercise — MCQs and CQs that combine ideas from several sections, with full solutions.
Writing rules
• NCTB terminology; give the English term in brackets the first time. Use textbook values and SI units; equations balanced with physical states; numbers and examples correct to the textbook. Never invent data; where books differ, say which value boards accept.
• Wherever two or more things are contrasted, use a comparison table under an <h4> heading containing "পার্থক্য", and register it with CMPT.push so it appears in Tools.
• MCQ quality: one clearly correct option, three plausible distractors of similar length; difficulty mix about 35% easy, 45% medium, 20% hard; about 8% in board multi-statement form (i, ii, iii → ক i ও ii / খ i ও iii / গ ii ও iii / ঘ i, ii ও iii); the correct option spread evenly (about 25% each of ক খ গ ঘ, never more than 3 in a row the same); explanations say why the answer is right and why the most tempting wrong option is wrong.
• CQ: an original stimulus (scenario, data table, experiment or described diagram) with ক knowledge (1), খ comprehension (2), গ application (3), ঘ higher ability (4); answers written the way an examiner wants them.
• Inside HTML strings write &lt; and &gt; for less-than and greater-than; use <sup>/<sub>; keep every table inside .table-wrap.
Visuals and simulations
How many and what kind. At least one visual for every lesson, two or more where an idea is hard to picture. Choose the kind that teaches the idea best for SUBJECT:
• Simulation (int) — the student changes a value with a slider, button or drag and sees the result change live (for example particles, waves, circuits, reactions, populations, graphs).
• Calculator (calc) — enter values, get the worked answer step by step with units.
• Diagram (2d) — a clean labelled SVG of apparatus, structure, process or graph.
• Animation (anim) — a process shown in steps with play/pause and a step stepper (ধাপ ১ → ২ → …), each step with a one-line explanation.
• 3D-style view (3d) — a rotatable shape drawn with CSS 3D or canvas projection, when the shape itself matters.
• Infographic (info) — a comparison, timeline, classification tree or flow chart.
Every practical or experiment in SUBTOPICS gets a step-by-step apparatus visual. Every formula that students calculate with gets a calculator. Every comparison table can also get a side-by-side infographic if it helps.
Contract. Each visual is VIS.<chapterId>_<name> = { t, k:[kinds], cap, html(), mount(el) }. html() returns the static markup (works with no script, so print and search still show it); mount(el) wires up the controls and may return a cleanup function that the app calls when the lesson closes. A lesson lists its visuals in v, and they appear inside the first block; {{v:id}} inside any block's HTML places a visual exactly there instead.
Shared toolkit. Put the reusable helpers in one window.VX object in the core and use them in every chapter instead of rewriting them: Bengali digits (bn), theme colours read from the CSS tokens (C), reduced-motion check, inline icons, a canvas set up for sharp rendering on high-density screens that refits on resize (cv, fit, onResize), an animation loop that stops when off-screen or hidden (anim), a play/pause button (pp), superscript/subscript and scientific-notation formatting (sup, sub, sci), a segmented control (seg, onSeg), an SVG wrapper with title for screen readers (svg), arrow markers, a seeded random-number generator so the same picture appears every time (rng), and pointer/touch dragging (drag). Add any subject-specific data or helpers (for chemistry: element table, electron configuration) to VX, not to a single visual.
Drawing rules.
• Colour only with the theme classes (fill .f-acc .f-accs .f-a2 .f-a2s .f-ok .f-bad .f-fg .f-mu .f-bg .f-sf .f-s2 .f-s3 .f-none, stroke .s-acc .s-a2 .s-fg .s-mu .s-ln) or the tokens, so every visual follows the chosen theme, including dark and high contrast. Dark "scientific" panels use --spec-bg/--spec-fg.
• Use a viewBox and 100% width so the visual fits a 360px column; minimum label size about 11px at that width; no label may overlap another label, a line or the edge — check each visual at 360px and at desktop width.
• Controls sit below the drawing in a row that wraps, each at least 44px tall, with Bengali labels and the current value shown.
• Show a live readout that explains what is happening in words ("তাপমাত্রা বাড়লে …"), not only a number.
• Respect reduced motion (show the final state and use the stepper instead of autoplay); pause animations that are off-screen; free timers and listeners in cleanup.
• The caption says in one or two sentences what the visual shows and how to use it.
• Values in simulations must follow the real laws (correct formula, correct units, sensible ranges); state any simplification in the caption.
Figure frame. Each visual is shown in a card with a header (title and kind chips: সিমুলেশন, ক্যালকুলেটর, চিত্র, অ্যানিমেশন, ৩D, ইনফোগ্রাফিক), the body, and the caption.
Build phases and the quality checklist
The whole app is too large for one reply, so build it in phases. Never shorten content to fit a reply — stop at a clean boundary instead and wait for me to say continue.
OUTPUT MODE = standalone
1. Phase 1 — plan. Print the section/lesson map built from SUBTOPICS (number, title, group A–E, tile symbol, importance, planned visuals per lesson) and the chosen design idea. Wait for "continue".
2. Phase 2 — core. Write the full HTML skeleton, all CSS with the seven themes, the chapter registry, the VX toolkit, and the complete app engine with every screen from §App structure, plus the chapter declaration and the first section with all its lessons, questions and visuals. The file must already open and work.
3. Phase 3 onward — sections. Two to four sections per reply, each as its own complete SEC.push with its visuals and comparison entries, in SUBTOPICS order, written to paste just before the "add new chapters here" marker (or, if you can produce files, the updated full file).
4. Last phase — summary and exercise sections, then the final checklist and the complete file assembled in order: core → chapter block(s) → template marker.
OUTPUT MODE = chapter-block
The core already exists in my file. Output only the new chapter: one <script> block that starts with HSC.chapter({...}) and contains every SEC.push, VIS and CMPT.push for this chapter, following the commented template at the end of my file, ready to paste below the "▼▼▼ নতুন অধ্যায় এই লাইনের নিচে ▼▼▼" marker. Use the same phases from step 1 (plan), then 3 and 4. Use only VX helpers and CSS classes that already exist; if a new helper is truly needed, define it inside the chapter block under a chapter-prefixed name.
After every phase, print this checklist with ✅ or ❌ for each line, and fix every ❌ before moving on:
[ ] Every SUBTOPICS line exists as a section or lesson with exactly the same number and title, in order; none added, none missing.
[ ] Every lesson has all 12 blocks filled to the sizes in §Content, at least one visual, 10–20 MCQs and 6–10 short questions.
[ ] Every section has its full question bank (including exactly 5 written questions of 2/3/5/7/10 marks), flashcards, formulas and exam analysis.
[ ] MCQ checks: four options each, answer index 0–3, difficulty mix about 35/45/20, correct options spread about evenly over ক খ গ ঘ (print the counts), about 8% multi-statement.
[ ] All ids unique across the file and prefixed with the chapter id; every lesson id referenced by an MCQ or comparison exists; every visual listed in a lesson is defined.
[ ] Settings → "অধ্যায় ও ফাইলের গঠন" would show zero problems; no console errors.
[ ] At 390px: no horizontal scroll on any screen, lesson or visual; no overlapping labels in any visual; all touch targets at least 44px.
[ ] Every visual mounts, responds to its controls, cleans up on leaving, and looks right in all seven themes and with reduced motion.
[ ] Progress, notes, highlights, bookmarks and quiz results survive a reload; the app works offline.
[ ] Facts, values, equations and units checked against the NCTB textbook; Bengali spelling and terminology consistent.
[ ] Running totals so far: sections, lessons, MCQs, short, CQ, written, flashcards, formulas, visuals.
Start now with Phase 1.
