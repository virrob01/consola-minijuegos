# Graph Report - consola-minijuegos  (2026-09-28)

## Corpus Check
- Corpus is ~10,790 words - fits in a single context window. You may not need a graph.

## Summary
- 129 nodes · 209 edges · 9 communities (7 shown, 2 thin omitted)
- Extraction: 83% EXTRACTED · 17% INFERRED · 0% AMBIGUOUS · INFERRED: 36 edges (avg confidence: 0.9)
- Token cost: 67,732 input · 0 output

## Community Hubs (Navigation)
- Serpientes y Escaleras
- Parqués: flujo de juego
- Buscaminas
- Memoria y récords
- Fichas y peones (SVG)
- Confeti de victoria
- Lanzador y páginas de juego

## God Nodes (most connected - your core abstractions)
1. `moveOnBoardPawn()` - 11 edges
2. `onRoll()` - 11 edges
3. `newGame()` - 10 edges
4. `renderPawns()` - 9 edges
5. `renderTokens()` - 9 edges
6. `checkWin()` - 8 edges
7. `newGame()` - 8 edges
8. `buildBoard()` - 7 edges
9. `onWin()` - 7 edges
10. `afterMove()` - 7 edges

## Surprising Connections (you probably didn't know these)
- `launchConfetti()` --implements--> `Confetti Win Celebration Pattern`  [INFERRED]
  games/buscaminas/index.html → index.html
- `saveBestIfNeeded()` --implements--> `localStorage Best Score Persistence`  [INFERRED]
  games/buscaminas/index.html → index.html
- `saveBestIfNeeded()` --implements--> `localStorage Best Score Persistence`  [INFERRED]
  games/memoria/index.html → index.html
- `setDieFace()` --implements--> `SVG Tokens and Pip Dice Pattern`  [INFERRED]
  games/parques/index.html → index.html
- `setDieFace()` --implements--> `SVG Tokens and Pip Dice Pattern`  [INFERRED]
  games/serpientes-escaleras/index.html → index.html

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **Confetti celebration duplicated across all games** — games_buscaminas_index_launchconfetti, games_memoria_index_launchconfetti, games_parques_index_launchconfetti, games_serpientes_escaleras_index_launchconfetti, index_confetti_celebration_pattern [INFERRED 0.95]
- **Dice turn flow: roll, animate, move, end turn** — games_parques_index_onroll, games_parques_index_animatediceroll, games_parques_index_moveonboardpawn, games_parques_index_aftermove, games_serpientes_escaleras_index_onroll, games_serpientes_escaleras_index_animatedieroll, games_serpientes_escaleras_index_moveplayerstepbystep, games_serpientes_escaleras_index_endturn [INFERRED 0.85]
- **Minesweeper reveal cascade** — games_buscaminas_index_oncellleftclick, games_buscaminas_index_revealcell, games_buscaminas_index_placemines, games_buscaminas_index_floodreveal, games_buscaminas_index_chordreveal, games_buscaminas_index_checkwin, games_buscaminas_index_onlose [EXTRACTED 1.00]

## Communities (9 total, 2 thin omitted)

### Community 0 - "Serpientes y Escaleras"
Cohesion: 0.11
Nodes (24): animateDieRoll(), cellCenterPx(), cellPosition(), createStaticTokenIcon(), drawLadder(), drawOverlay(), drawSnake(), endTurn() (+16 more)

### Community 1 - "Parqués: flujo de juego"
Cohesion: 0.13
Nodes (23): afterMove(), animateDiceRoll(), clearHighlights(), currentColor(), getPlayerName(), log(), moveOnBoardPawn(), newGame() (+15 more)

### Community 2 - "Buscaminas"
Cohesion: 0.13
Nodes (22): buildBoardDOM(), checkWin(), chordReveal(), DIFFICULTIES, fitCellSize(), floodReveal(), forEachNeighbor(), formatTime() (+14 more)

### Community 3 - "Memoria y récords"
Cohesion: 0.16
Nodes (16): bestKey(), loadBest(), saveBestIfNeeded(), shuffle(), bestKey(), buildBoard(), formatTime(), loadBest() (+8 more)

### Community 4 - "Fichas y peones (SVG)"
Cohesion: 0.14
Nodes (13): COLORS_CFG, createStaticTokenIcon(), createTokenSVG(), ensurePawnElement(), getCellCoordForStep(), onPawnClick(), renderPawns(), tokenSvgMarkup() (+5 more)

### Community 5 - "Confeti de victoria"
Cohesion: 0.33
Nodes (4): launchConfetti(), launchConfetti(), launchConfetti(), Confetti Win Celebration Pattern

### Community 6 - "Lanzador y páginas de juego"
Cohesion: 0.53
Nodes (6): Buscaminas (Minesweeper) Game Page, Memoria (Memory) Game Page, Parques (Parcheesi) Game Page, Serpientes y Escaleras (Snakes and Ladders) Game Page, Consola Minijuegos Launcher, Self-Contained Single-File Game Pages

## Knowledge Gaps
- **9 isolated node(s):** `DIFFICULTIES`, `SHAPES`, `THEMES`, `COLORS_CFG`, `SAFE_INDICES` (+4 more)
  These have ≤1 connection - possible missing edges. (Counts symbols only; 30 node(s) total have ≤1 connection when file, concept and rationale nodes are included.)
- **2 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `onWin()` connect `Memoria y récords` to `Parqués: flujo de juego`, `Buscaminas`, `Confeti de victoria`?**
  _High betweenness centrality (0.321) - this node is a cross-community bridge._
- **Why does `triggerWin()` connect `Parqués: flujo de juego` to `Memoria y récords`, `Confeti de victoria`?**
  _High betweenness centrality (0.306) - this node is a cross-community bridge._
- **Why does `checkWin()` connect `Buscaminas` to `Memoria y récords`?**
  _High betweenness centrality (0.271) - this node is a cross-community bridge._
- **Are the 3 inferred relationships involving `onRoll()` (e.g. with `onRoll()` and `LADDERS`) actually correct?**
  _`onRoll()` has 3 INFERRED edges - model-reasoned connections that need verification._
- **What connects `DIFFICULTIES`, `SHAPES`, `THEMES` to the rest of the system?**
  _9 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Serpientes y Escaleras` be split into smaller, more focused modules?**
  _Cohesion score 0.10837438423645321 - nodes in this community are weakly interconnected._
- **Should `Parqués: flujo de juego` be split into smaller, more focused modules?**
  _Cohesion score 0.1282051282051282 - nodes in this community are weakly interconnected._