<script>
  import Board from "./Board.svelte";
  import { TicTacToe } from "./board";
  let message;
  let game = createGame();
  function createGame() {
    message = null;
    return new TicTacToe({
      onWin(winner) {
        message = `${winner} gana!`;
      },
      onTie() {
        message = `Empate a la versh`;
      }
    });
  }
  function newGame() {
    game = createGame();
  }
</script>

<style>
  h2 {
    display: inline;
  }
  body {
    background-color: red;
  }
</style>

<svelte:head>
	<title>Tic Tac Toe</title>
</svelte:head>

<h1>Tic Tac Toe</h1>

<button on:click={newGame}>Juego nuevo</button>

{#if message}
  <h2>{message}</h2>
{/if}

<Board {game} />