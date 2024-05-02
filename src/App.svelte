<script>
  import Team from './lib/Team.svelte';
  let blueScore = 20;
  let redScore = 20;
  $: redWon = blueScore === 0;
  $: blueWon = redScore === 0;
  $: gameOver = redWon || blueWon;
  function newGame() {
    redScore = 20;
    blueScore = 20;
  }
</script>

<div class="row mt-2">
  <div class="col">
    <h1 class="text-center">MTG COUNTER</h1>
  </div>
</div>
<div class="row">
  <Team {gameOver} team="Red" bind:score={redScore} />
  <Team {gameOver} team="Blue" bind:score={blueScore} />
</div>
<div class="row mt-4">
  <div class="col">
    {#if blueWon}
      <h2 class="text-center text-primary">Blue Won</h2>
    {:else if redWon}
      <h2 class="text-center text-primary">Red Won</h2>
    {:else}
      <h2 class="text-center text-primary">Playing: Red VS Blue</h2>
    {/if}
  </div>
</div>
<div class="row mt-4">
  <div class="col">
    {#if !gameOver}
      <button class="btn btn-warning w-100" on:click={newGame}
        >Reset Game</button
      >
    {:else}
      <button class="btn btn-success w-100" on:click={newGame}>New Game</button>
    {/if}
  </div>
</div>
