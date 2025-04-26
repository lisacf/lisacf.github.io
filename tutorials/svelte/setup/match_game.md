## Technology Stack

- **SvelteKit**  
  - File-based routing, built-in dev server & adapter support  
  - Zero-config TypeScript and environment support  
- **Vitest**  
  - Native Vite integration (used by SvelteKit)  
  - Fast in-memory unit & integration tests  
  - Works with `@testing-library/svelte` for component testing  
- **Playwright**  
  - Reliable end-to-end browser testing across Chromium, Firefox, WebKit  
  - Automates user flows (tile swapping, match detection, animations)  

> **Yes**—this combo gives a first-class developer experience and lets you drive all game logic and UI through tests from Day 1.

---

## Project Plan

| Phase                                | Goals                                                                 | Deliverables                                                                                                                                  | Testing Focus                                                                                  |
|--------------------------------------|-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| **1. Environment & Scaffolding**      | • Bootstrap SvelteKit project<br>• Configure Vitest & Playwright      | • `npm init svelte@next` project<br>• `vitest.config.ts`, Playwright setup script                                                            | • Smoke test: “app loads” unit test<br>• Playwright “homepage renders”                          |
| **2. Core Grid Layout**              | • Render an M×N grid of tiles<br>• Style tiles (CSS/Tailwind)         | • `Grid` Svelte component<br>• Static grid snapshot                                                                                          | • Unit tests for correct cell count<br>• Snapshot tests via Vitest                               |
| **3. Tile Swap Interaction**         | • Click/drag to swap two adjacent tiles<br>• Swap animation           | • `Tile` & `Grid` event handlers<br>• Swap state machine                                                                                     | • Unit tests for swap logic (indexes, bounds)<br>• Playwright flow: “swap two tiles”            |
| **4. Match Detection & Resolution**   | • Detect 3-in-a-row (H/V)<br>• Remove matched tiles<br>• Refill logic  | • `matchEngine` module (pure functions)<br>• Refill algorithm                                                                                 | • Unit tests on `matchEngine` patterns<br>• Playwright: “make a match → tiles disappear & refill” |
| **5. Scoring & Combo Logic**          | • Base points per tile<br>• Bonuses for cascades/combos               | • `ScoreBoard` component<br>• Combo multiplier logic                                                                                         | • Unit tests for scoring rules<br>• E2E: “chain two matches → correct score”                    |
| **6. UI Polish & Animations**         | • Smooth transitions (Svelte `animate`/`transition`)<br>• Responsive  | • CSS animations, mobile breakpoints                                                                                                         | • Playwright visual checks (animation end state)<br>• Accessibility smoke tests                |
| **7. Test Coverage & CI/CD**         | • Integrate Vitest + Playwright in GitHub Actions<br>• Coverage gates | • `.github/workflows/tests.yml`<br>• Badges in README                                                                                         | • CI build passes on every PR<br>• Coverage ≥ 80%                                               |
| **8. Feature Extensions**            | • Power-ups, special tiles<br>• Level progression, themes             | • New Svelte components & logic modules                                                                                                       | • Unit tests per new feature<br>• E2E: full-game playthrough test                              |

---

## Testing Strategy

1. **Test-First Development**  
   - Write a failing test for each piece of game logic (swap, match, score)  
   - Implement just enough code to pass  
   - Refactor safely, backed by tests  

2. **Component-Level**  
   - Use Vitest + `@testing-library/svelte`  
   - Test props, events & DOM updates in isolation  

3. **Pure-Function Modules**  
   - Extract grid/match/score logic into small functions  
   - Cover edge cases: no matches, boundary swaps, chain reactions  

4. **End-to-End**  
   - Playwright scripts mirror real user behavior  
   - Automate flows: start game → swap tiles → detect match → verify score  

---

## Continuous Integration & Workflow

- **GitHub Actions**  
  - Run `vitest --coverage` on every push/PR  
  - Launch headless browser for Playwright tests  
  - Fail build on test failures or coverage drop  

- **Branching Model**  
  - `main`: always green (protected)  
  - Feature branches → PR → CI → Code review → Merge  

- **Developer Feedback Loop**  
  - Fast Vitest watch mode (`npm run test:watch`)  
  - Periodic full-suite CI runs for end-to-end validation  

---

## Next Steps

1. **Initialize** your SvelteKit repo & install `vitest`, `@testing-library/svelte`, `playwright`.  
2. **Commit** your first “renders homepage” test—watch it fail and then pass.  
3. **Lay out** the grid component and jump into Phase 2.

Let me know if you’d like example test code snippets or CI config details!
