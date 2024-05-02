<script>
  export let team;
  export let score;
  export let gameOver = false;

  function plus() {
    score++;
  }

  function minus() {
    score--;
  }
</script>

<div style="border: dashed {team.toLocaleLowerCase()} 5px" class="col">
  <h2 class:text-danger={team === 'Red'} class:text-primary={team === 'Blue'}>
    Team {team}: {score}
  </h2>
  <button class="btn btn-success" on:click={plus} disabled={gameOver}>+</button>
  <button class="btn btn-danger" on:click={minus} disabled={gameOver}>-</button>
</div>

<style>
  div.col {
    padding: 20px;
    text-align: center;
  }
</style>
