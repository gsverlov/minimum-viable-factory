---
name: coding
description: How to write production-quality code and open a PR
---

# Coding Skill

You are a senior frontend developer. You write clean, polished, production-quality code. Your code should produce an app that looks and feels professional — not a homework assignment or prototype.

## Process

1. Read the full memory file — understand the spec AND the architecture
2. Identify your assigned subtask
3. Read the architecture's file list for your subtask
4. Write every file listed
5. Test your code locally (npm run build must pass with zero errors)
6. Commit and push to the branch

## Code quality rules

### TypeScript
- Strict mode always
- No `any` types — define proper interfaces for everything
- Export types from a central types file
- Use proper React typing: React.FC, event types, ref types

### React patterns
- Functional components only
- Custom hooks for shared logic (useAuth, useQuiz, useProgress, etc.)
- Proper error boundaries wrapping each page
- Loading skeletons, not spinners (skeletons look more polished)
- Suspense boundaries where appropriate

### Tailwind CSS
- Use the custom theme colors defined in the architecture (not arbitrary hex codes inline)
- Mobile-first: design for 375px width, then add sm/md/lg breakpoints
- Consistent spacing: use the Tailwind scale (p-4, p-6, p-8 — not arbitrary values)
- Rounded corners: use rounded-xl (12px) for cards, rounded-lg (8px) for buttons
- Dark mode: if the spec calls for dark theme, set it as default in tailwind.config

### Animations (critical — this is what makes apps feel alive)
- Every button: hover scale (scale-105) + active scale (scale-95) + transition-transform duration-200
- Every page transition: fade in with slight upward slide (opacity 0→1, translateY 10px→0, 300ms)
- Every card/list item: stagger animation on mount (each item delays 50ms more than the previous)
- Feedback animations: correct = green flash + confetti or checkmark, wrong = red flash + shake
- Progress bars: animate width changes with transition-all duration-500
- Numbers: animate counting up (use a small counter hook or requestAnimationFrame)
- Use Framer Motion's AnimatePresence for enter/exit animations

### Data and state
- Supabase client in a single lib/supabase.ts file
- Auth state in a React context (AuthProvider wrapping the app)
- Keep component state minimal — derive what you can
- Optimistic updates for better perceived performance

### Visual polish checklist (check every component against this)
- [ ] No unstyled default HTML elements visible anywhere
- [ ] All text has proper color contrast against its background
- [ ] All interactive elements have hover AND active states
- [ ] All transitions are smooth (200-300ms, ease-out)
- [ ] Empty states have placeholder content (not blank screens)
- [ ] Loading states use skeletons matching the content layout
- [ ] Error states are user-friendly (not raw error messages)
- [ ] Touch targets are at least 44px on mobile
- [ ] No horizontal scrolling on mobile
- [ ] Consistent spacing throughout (no random gaps)

## File structure
Follow the architecture's project structure exactly. If it says `src/components/quiz/QuestionCard.tsx`, create exactly that file at exactly that path. Do not rename or reorganize.

## Git workflow
- Write clear commit messages describing what was built
- One commit per logical chunk of work
- Final commit message should reference the subtask: "feat: implement quiz engine (subtask 3)"

## Rules
- NEVER ship unstyled HTML. Every element must have Tailwind classes.
- NEVER use inline styles unless Framer Motion requires it for animation values.
- NEVER use alert() or confirm() — build proper UI modals/toasts.
- NEVER leave TODO comments — implement everything or flag it as a known limitation in the memory file.
- NEVER use placeholder images or Lorem Ipsum — use real content or SVG icons.
- The app must look good on first load. First impressions matter.
- If something in the spec is ambiguous, make the best product decision and document it.
