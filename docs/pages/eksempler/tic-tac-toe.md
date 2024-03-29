---
layout: page
permalink: /eksempler/tic-tac-toe
exclude: true
title: Tic-tac-toe
---

Her har vi laget en enkel versjon av tic-tac-toe (eller tripp-trapp-tresko, som det heter på norsk).

Dette er et eksempel på hvordan alt spiller sammen for å gi en nettside som har form, farge, og oppførsel.

Det er ikke det peneste spillet i verden - kan du gjøre det penere?

I tillegg har vi 2 `<input>`-felter som ikke gjør noe - kan du gjøre slik at navnet til spilleren blir vist når spillet er over?

**Utfordring:** Kan du gjøre slik at brettet er større enn 3x3, at spilleren selv kan skrive inn hvor stor han vil ha den, 9x9 for eksempel?
(Dette vil kreve en stor omskriving av hele spillet, og vil være veldig utfordrende!)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Tripp trapp tresko!</title>
    <style>
      body {
        display: table;
        margin: auto;
      }

      .name-fields {
        max-width: 30em;
      }

      .input-with-label {
        display: flex;
        flex-direction: column;
      }

      .game-area {
        display: flex;
        flex-direction: column;
      }

      .game-grid {
        display: grid;
        gap: 2em;
        grid-template-columns: repeat(3, 1fr);
      }

      .game-cell {
        height: 5em;
        width: 5em;
      }

      .game-over {
        display: none;
      }
    </style>

    <script>
      // spillbrettet er representert internt som en liste med 9 elementer, men er en 3x3 matrise på nettsiden
      let gameState = initGameState();
      let currentPlayer = "X";
      let xPlayerName = "";
      let oPlayerName = "";
      let gameOver = false;

      // vi må vente til siden har lastet ferdig før vi kan gjøre noe
      window.addEventListener("load", function () {
        renderGameState();
      });

      // funksjon som setter riktige verdier i
      function renderGameState() {
        for (let y = 1; y < 4; y++) {
          for (let x = 1; x < 4; x++) {
            const currentCell = getGameCell(x, y);
            const currentIndex = getIndexFromCoordinates(x, y);
            currentCell.innerHTML = gameState[currentIndex];
          }
        }
        document.getElementById("current-player-name").innerHTML =
          currentPlayer;

        gameOver = checkWinCondition();
        if (gameOver) {
          currentPlayer = getNextPlayer(currentPlayer);
          document.getElementById("winning-player-name").innerHTML =
            currentPlayer;
          const gameOverText = document.getElementsByClassName("game-over")[0];
          gameOverText.style.display = "block";
        }
      }

      // funksjon som kalles når man klikker en celle
      function clickCell(y, x) {
        const currentIndex = getIndexFromCoordinates(x, y);
        const currentCellState = gameState[currentIndex];
        if (currentCellState !== " " || gameOver) {
          return;
        }
        gameState[currentIndex] = currentPlayer;
        currentPlayer = getNextPlayer(currentPlayer);
        renderGameState();
      }

      // hjelpefunksjon for å få tak i en celle med koordinater
      function getGameCell(x, y) {
        const selector = "game-cell-" + y + "-" + x;
        return document.getElementById(selector);
      }

      // hjelpefunksjon for å finne neste spiller
      function getNextPlayer(player) {
        if (player === "X") {
          return "O";
        } else {
          return "X";
        }
      }

      // hjelpefunksjon for å transformere fra 2 dimensjonelle koordinater til 1 dimensjonell indeks
      function getIndexFromCoordinates(x, y) {
        const i = y - 1;
        const j = x - 1;
        return i * 3 + j;
      }

      // funksjon som sjekker om spillet er over
      function checkWinCondition() {
        const rowWin = checkRows();
        const columnWin = checkColumns();
        const diagonalWin = checkDiagonals();
        return rowWin || columnWin || diagonalWin;
      }

      // hjelpefunksjon som sjekker radene
      function checkRows() {
        for (let y = 1; y < 4; y++) {
          const firstIndex = getIndexFromCoordinates(1, y);
          const secondIndex = getIndexFromCoordinates(2, y);
          const thirdIndex = getIndexFromCoordinates(3, y);
          const currentRow = [
            gameState[firstIndex],
            gameState[secondIndex],
            gameState[thirdIndex],
          ];
          if (currentRow.some((cell) => cell === " ")) {
            continue;
          }
          if (
            currentRow.every((cell) => cell === "X") ||
            currentRow.every((cell) => cell === "Y")
          ) {
            return true;
          }
        }
        return false;
      }

      // hjelpefunksjon som sjekker kolonnene
      function checkColumns() {
        for (let x = 1; x < 4; x++) {
          const firstIndex = getIndexFromCoordinates(x, 1);
          const secondIndex = getIndexFromCoordinates(x, 2);
          const thirdIndex = getIndexFromCoordinates(x, 3);
          const currentColumn = [
            gameState[firstIndex],
            gameState[secondIndex],
            gameState[thirdIndex],
          ];
          if (currentColumn.some((cell) => cell === " ")) {
            continue;
          }
          if (
            currentColumn.every((cell) => cell === "X") ||
            currentColumn.every((cell) => cell === "Y")
          ) {
            return true;
          }
        }
        return false;
      }

      // hjelpefunksjon som sjekker diagonalene
      function checkDiagonals() {
        let firstIndex = getIndexFromCoordinates(1, 1);
        let secondIndex = getIndexFromCoordinates(2, 2);
        let thirdIndex = getIndexFromCoordinates(3, 3);
        let diagonal = [
          gameState[firstIndex],
          gameState[secondIndex],
          gameState[thirdIndex],
        ];
        const firstDiagonalWin = checkDiagonal(diagonal);

        firstIndex = getIndexFromCoordinates(1, 3);
        secondIndex = getIndexFromCoordinates(2, 2);
        thirdIndex = getIndexFromCoordinates(3, 1);
        diagonal = [
          gameState[firstIndex],
          gameState[secondIndex],
          gameState[thirdIndex],
        ];
        const secondDiagonalWin = checkDiagonal(diagonal);

        return firstDiagonalWin || secondDiagonalWin;
      }

      // hjelpefunksjon som sjekker en diagonal
      function checkDiagonal(diagonal) {
        if (!diagonal.some((cell) => cell === " ")) {
          if (
            diagonal.every((cell) => cell === "X") ||
            diagonal.every((cell) => cell === "Y")
          ) {
            return true;
          }
        }
        return false;
      }

      // hjelpefunksjon som uthenter en spillers navn
      function getPlayerName(player) {
        if (player === "X") {
          if (xName == null || xName.length === 0) {
            return "X";
          }
        }
        if (player === "O") {
        }
      }

      // funksjon som restarter spillet
      function restartGame() {
        currentPlayer = "X";
        gameState = initGameState();
        const gameOverText = document.getElementsByClassName("game-over")[0];
        gameOverText.style.display = "none";
        renderGameState();
      }

      // funksjon som nullstiller spillebrettet
      function initGameState() {
        return [
          // x 1    2    3      y
          " ",
          " ",
          " ", // 1
          " ",
          " ",
          " ", // 2
          " ",
          " ",
          " ", // 3
        ];
      }
    </script>
  </head>

  <body>
    <h1>Tripp trapp tresko</h1>

    <section class="name-fields">
      <label class="input-with-label" for="player-x">
        <b>Spiller X: </b>
        <input type="text" name="player-x" id="player-x-name-input" />
      </label>
      <br />
      <label class="input-with-label" for="player-o">
        <b>Spiller O: </b>
        <input type="text" name="player-o" id="player-o-name-input" />
      </label>
    </section>

    <hr />

    <section class="game-section">
      <div id="current-player">
        <span id="current-player-name"></span> sin tur
      </div>

      <div class="game-grid">
        <!-- første rad -->
        <button
          class="game-cell"
          type="button"
          id="game-cell-1-1"
          onclick="clickCell(1, 1)"
        ></button>
        <button
          class="game-cell"
          type="button"
          id="game-cell-1-2"
          onclick="clickCell(1, 2)"
        ></button>
        <button
          class="game-cell"
          type="button"
          id="game-cell-1-3"
          onclick="clickCell(1, 3)"
        ></button>

        <!-- andre rad -->
        <button
          class="game-cell"
          type="button"
          id="game-cell-2-1"
          onclick="clickCell(2, 1)"
        ></button>
        <button
          class="game-cell"
          type="button"
          id="game-cell-2-2"
          onclick="clickCell(2, 2)"
        ></button>
        <button
          class="game-cell"
          type="button"
          id="game-cell-2-3"
          onclick="clickCell(2, 3)"
        ></button>

        <!-- tredje rad -->
        <button
          class="game-cell"
          type="button"
          id="game-cell-3-1"
          onclick="clickCell(3, 1)"
        ></button>
        <button
          class="game-cell"
          type="button"
          id="game-cell-3-2"
          onclick="clickCell(3, 2)"
        ></button>
        <button
          class="game-cell"
          type="button"
          id="game-cell-3-3"
          onclick="clickCell(3, 3)"
        ></button>
      </div>

      <hr />
      <div class="game-over" id="game-over-text">
        Spillet er over!
        <span id="winning-player-name"></span> vant!
      </div>

      <button type="button" id="restart-button" onclick="restartGame()">
        Restart
      </button>
    </section>
  </body>
</html>
```
