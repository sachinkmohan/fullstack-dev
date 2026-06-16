# PRD: Complete the React Hooks Interview-Prep Curriculum

> Captured via `/to-prd`. Adapted from the standard feature-PRD template — this is a content/curriculum task, not a software feature. Sections that don't apply (testing seams, API contracts) are repurposed.

## Problem Statement

I am preparing for React engineering interviews in the next 1–4 weeks. I've already shipped components using `useState` and `useEffect`, but I feel shaky on the deeper hooks: dependency arrays and cleanup, `useMemo` / `useCallback`, `useReducer` / `useContext`, and `useRef` / custom hooks. I need a complete, self-paced learning path that builds up to interview-ready answers — not just *how* to call each hook, but *why* they work the way they do.

The first three lessons exist (snapshot model → stale closures → updater functions). I need the remaining curriculum generated in the same style so I can work through them on my own time.

## Solution

A complete set of self-contained HTML lessons in `react/hooks/lessons/`, each:

- Teaching **one concept** at a time (per [`NOTES.md`](./NOTES.md) pacing rules)
- Leading with an analogy, puzzle, or known JavaScript fact before any React-specific syntax
- Including a 4-question quiz with inline feedback and a final score
- Linking a single primary source from [`RESOURCES.md`](./RESOURCES.md)
- Matching the visual template of lessons 0001–0003 (Georgia serif body, blue accent, mono code)
- Cross-linked via prev / next nav

When the curriculum is complete, I should be able to walk into a React interview and confidently answer the "why" questions for every major hook — including the gotcha follow-ups.

## User Stories (Lessons)

Each lesson is one user story. Numbering continues from existing lessons.

1. **(Done)** As a learner, I want to understand that each render is a frozen snapshot, so that every other hook concept has a foundation. → `0001-each-render-is-a-snapshot.html`
2. **(Done)** As a learner, I want to spot stale closures and name three fixes, so that I can debug the most common hook bug. → `0002-stale-closures.html`
3. **(Done)** As a learner, I want to use updater functions to escape the snapshot, so that I can safely derive new state from old. → `0003-updater-functions.html`
4. As a learner, I want to re-frame `useEffect` as **synchronization with an external system** rather than a lifecycle event, so that I stop reaching for it as "componentDidMount". → `0004-effects-as-synchronization.html`
5. As a learner, I want to understand what goes into the **dependency array** and why the linter is strict about it, so that I can predict when an effect re-runs. → `0005-dependency-array.html`
6. As a learner, I want to understand **cleanup functions and Strict Mode's double-fire**, so that I can answer "why does my fetch run twice in dev?". → `0006-cleanup-and-strict-mode.html`
7. As a learner, I want to learn the **"You might not need an Effect"** patterns (derived state, event handlers, parent-driven resets), so that I can refactor accidental effects on a whiteboard. → `0007-you-might-not-need-an-effect.html`
8. As a learner, I want to understand **`useRef` as the escape hatch** from the snapshot model, so that I can hold mutable values and DOM nodes without triggering re-renders. → `0008-useref-the-escape-hatch.html`
9. As a learner, I want to know when to reach for **`useReducer` over `useState`**, so that I can defend the choice in an interview. → `0009-usereducer.html`
10. As a learner, I want to understand **`useContext` and its real cost** (every consumer re-renders), so that I can name common anti-patterns. → `0010-usecontext.html`
11. As a learner, I want to understand **referential equality** (`Object.is` on every render), so that the reason `useMemo` / `useCallback` / `React.memo` exist becomes obvious. → `0011-referential-equality.html`
12. As a learner, I want to know **when `useMemo` actually helps vs when it's noise**, so that I don't memoize everything by reflex. → `0012-usememo.html`
13. As a learner, I want to see **`useCallback` as `useMemo` for functions**, so that I understand both with one mental model. → `0013-usecallback.html`
14. As a learner, I want to build a **custom hook** from scratch and articulate that they share *logic*, not *state*, so that I can answer the most common senior-tier interview question. → `0014-custom-hooks.html`
15. As a learner, I want to understand **the Rules of Hooks** (call order, no conditionals, no loops) and *why* they exist, so that I can explain the rules from first principles. → `0015-rules-of-hooks.html`

## Implementation Decisions

- **Template parity.** Every lesson uses the exact CSS block from lessons 0001–0003 (root variables, body, progress, h1/h2, pre/code, box, puzzle, quiz, primary-source, nav). Lesson-specific CSS additions (e.g., a "snapshot card" visual) are added inline only when the lesson needs them.
- **One concept rule.** Per the [`0002-lesson-1-too-dense.md`](../typescript/generics/learning-records/0002-lesson-1-too-dense.md) learning record (carried over from the TypeScript workspace), each lesson teaches exactly one new concept. Adjacent concepts are explicitly deferred to a later lesson.
- **Quiz format.** 4 questions per lesson, each with 4 options, exactly one correct. Feedback strings are written so a wrong answer corrects the user's likely misconception. Final score message varies by score (1/4 through 4/4).
- **Primary source per lesson.** One canonical link only. Prefer `react.dev` for official mental models; Dan Abramov's `overreacted.io` for closures and memoization deep dives. Reading time annotated.
- **Nav.** Every lesson links the previous and next lesson by anchor. Lesson 15 has no "next".
- **Visual special cases.** Likely candidates for extra CSS / SVG:
  - Lesson 5 (dep array): a "diff" visual showing React comparing dep arrays.
  - Lesson 6 (cleanup): a timeline showing setup → cleanup → setup in Strict Mode.
  - Lesson 8 (useRef): a "box that survives renders" illustration.
  - Lesson 11 (referential equality): two object boxes with an "Object.is" arrow showing `false`.
  - Lesson 15 (rules of hooks): a numbered list showing call-order matching across renders.
- **Reference docs.** As the curriculum grows, extract repeated content into `reference/` documents the lessons link to. Likely first reference: a **hooks cheat sheet** (one-line "what it does / when to reach for it" per hook) and a **glossary** (snapshot, closure, dependency, referential equality, etc.). Build these after the lessons land — don't pre-extract.
- **Mission alignment.** Every lesson should call out the interview angle in a "Why interviewers love this" section, naming the classic question the concept unlocks.

## Testing Decisions

Repurposed for this content workspace:

- **What "good" looks like for a lesson.** A lesson is correct when (a) the single concept is stated in one sentence in a highlight box, (b) the example code is the minimum that demonstrates the concept, (c) the quiz only tests what was explicitly taught in this lesson, and (d) the primary source link goes directly to the most relevant section (not a homepage).
- **Manual verification.** After generating each lesson, open it in a browser, take all 4 quiz questions both correctly and incorrectly, and confirm the feedback and final score render. The user does this — it's the "feedback loop" for catching density / clarity issues.
- **Prior art.** [`0002-generics-from-scratch.html`](../typescript/generics/lessons/0002-generics-from-scratch.html) in the TypeScript workspace is the gold-standard reference for tone, density, and structure. New lessons should match it.
- **Density check.** Use the [`0002-lesson-1-too-dense.md`](../typescript/generics/learning-records/0002-lesson-1-too-dense.md) record as the bar: if a lesson introduces more than one new concept, or has more than ~3 short code blocks before the first quiz hint, it's too dense and should be split.

## Out of Scope

- **React Server Components, server actions, `use()`, `useActionState`, `useOptimistic`, the React compiler.** Modern React 19 surface area is outside the interview prep scope unless the user requests it later.
- **State management libraries** (Redux, Zustand, Jotai, TanStack Query) — `useReducer` + `useContext` is the cap.
- **Class components and lifecycle methods**, except as a brief contrast inside lesson 1 (already covered) and possibly lesson 4.
- **A full sample app or project scaffold.** Lessons stand alone — there's no app to build.
- **Automated tests for the HTML lessons.** They're static documents. Manual review in the browser is the loop.
- **Reference documents** (cheat sheet, glossary) — earmarked for a follow-up pass after lessons land.

## Further Notes

- **Issue-tracker publishing.** `gh` CLI is not authenticated in this environment, so this PRD is saved locally as `react/hooks/PRD-remaining-lessons.md` instead of being pushed to GitHub. To publish it: `gh auth login`, then `gh issue create --title "Complete React hooks curriculum (lessons 4–15)" --body-file react/hooks/PRD-remaining-lessons.md --label ready-for-agent` (assuming the repo's labels include `ready-for-agent`).
- **Source of truth for style.** Lessons 0001 and 0002 are the reference for HTML structure, CSS variables, and quiz JS. Lesson 0003 is leaner and a good reference for the shorter format. Copy from these — don't invent.
- **Sequencing rationale.** Lessons 1–3 establish the snapshot mental model. Lessons 4–7 are the `useEffect` arc — the highest-value interview territory. Lesson 8 introduces the escape hatch. Lessons 9–10 cover the bigger state primitives. Lessons 11–13 are the memoization arc, sequenced so referential equality is grokked before `useMemo` / `useCallback` are introduced. Lessons 14–15 close out with custom hooks and the rules.
- **Pacing if interview window tightens.** If interview prep time collapses, the highest-leverage subset is: 4, 5, 7, 11, 14. The "why" answers in these unlock the most senior-tier credit. The rest can be skimmed.
- **Workspace files already in place.** `MISSION.md`, `NOTES.md`, `RESOURCES.md`, and lessons 0001–0003 are written. A future session should read those four files first before generating new lessons.
