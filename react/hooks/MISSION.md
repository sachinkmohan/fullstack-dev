# Mission: React Hooks

## Why
Active interview prep — interviewing in the next 1–4 weeks. Need to articulate *why* hooks work the way they do, not just call them. The goal is to walk into a React interview and confidently answer questions about effects, closures, memoization, and custom hooks — including the "gotcha" questions that separate intermediate engineers from senior ones.

## Success looks like
- Can explain in plain English why `useEffect` has a dependency array and what happens when you get it wrong.
- Can describe a stale closure bug and three ways to fix it.
- Can say *when* `useMemo` / `useCallback` actually help — and when they're noise.
- Can build a custom hook from scratch and justify the abstraction.
- Can describe when to reach for `useReducer` vs `useState`, and `useContext`'s real cost.
- Can answer "why these rules of hooks?" with the call-order explanation.

## Constraints
- 1–4 week interview window — prioritise the highest-leverage interview topics first.
- Already shipped `useState` / `useEffect` in real code — don't waste time on the basics.
- Learning style: tiny interactive exercises, reading + reference docs, analogies to existing knowledge.
- Lessons must be short and enjoyable. One concept per lesson.

## Out of scope
- React Server Components, server actions, the React compiler — only if it comes up in an interview.
- Redux, Zustand, TanStack Query, and other state libraries.
- Class components and lifecycle methods (except as historical contrast where it sharpens hook understanding).
- Building a full app — we're learning hooks, not React project architecture.
