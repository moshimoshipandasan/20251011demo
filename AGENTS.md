# Repository Guidelines

This repository delivers a 2D マインクラフト風ゲームのMVP that runs in the browser via Vite + TypeScript + Phaser 3 and publishes to GitHub Pages. Use this guide while contributing new features or refactors.

## Project Structure & Module Organization
- `src/main.ts`: bootstraps Phaser and registers scenes.
- `src/scenes/GameScene.ts`: core gameplay loop, player control, world integration.
- `src/game/`: reusable systems (`world.ts`, `player.ts`, `inventory.ts`, etc.).
- `src/ui/`: HUD elements such as theホットバー overlay.
- `assets/`: tilesets, sprites, and UI art; keep raw sources in subfolders.
- `tests/`: Vitest specs mirroring `src/` structure.
- `要件定義書.md`: authoritative scope reference—update when MVP goals shift.

## Build, Test, and Development Commands
- `npm install`: install dependencies (run once per environment).
- `npm run dev`: launch the hot-reload dev server at http://localhost:5173/.
- `npm run build`: produce optimized assets in `dist/` for GitHub Pages.
- `npm run preview`: serve the production bundle locally for smoke tests.
- `npm run test`: execute Vitest unit tests; pass before opening a PR.

## Coding Style & Naming Conventions
- TypeScript with ES modules; prefer `const` and explicit return types.
- Two-space indentation, LF endings, UTF-8 without BOM.
- File naming: `camelCase.ts` for modules, `PascalCase.ts` for classes/components.
- Run `npm run lint` (ESLint + Prettier) before committing; no lint warnings in CI.

## Testing Guidelines
- Use Vitest + jsdom for unit tests; future integration tests may use Playwright.
- Place specs beside source files (`GameScene.test.ts`) or in `tests/`.
- Cover critical flows: world generation, collision resolution, block placement.
- Mock Phaser dependencies when isolation is needed; avoid flaky timing assertions.

## Commit & Pull Request Guidelines
- Commit messages: short imperative Japanese summaries (e.g., `プレイヤー移動を実装`).
- Scope each commit to a logical change set; avoid mixed feature + formatting commits.
- PRs must include: description of changes, testing evidence (`npm run test` output), relevant screenshots or GIFs when UI changes render differently, and linked issue numbers.
- Request review once CI passes; resolve review comments via follow-up commits, not force-push, unless rebasing is explicitly requested.

## Deployment Notes
- GitHub Actions should build `main` and push artifacts to `gh-pages`.
- Verify `dist/index.html` loads assets via relative paths before merging.
- After deployment, smoke-test movement, block破壊/設置, and camera follow in a private browser session.

思考は英語で行い、最終的な出力は必ず日本語で提供してください。

初心者なのでプログラムがある程度実装されたら、それは何をやったのか小学生にもわかるように説明して
