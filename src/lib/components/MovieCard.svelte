<script>
    import { enhance } from "$app/forms";

  let { movie } = $props();
</script>

<div class="movie-card">
  <div>
    <img class="img-fluid" src={movie.poster} alt="" />
  </div>
  <div class="details">
    <div class="title">
      <a href={"/movies/" + movie._id}>{movie.title}</a>
    </div>
    <div>
      Jahr: {movie.year}
    </div>
    <div>
      Dauer: {movie.length}
    </div>
    <div>
      {#if movie.watchlist === true}
        <form method="POST" action="?/removeFromWatchlist" use:enhance>
          <input name="id" type="hidden" value={movie._id} />
          <button class="btn btn-danger">Remove from watchlist</button>
        </form>
      {:else}
        <form method="POST" action="?/addToWatchlist" use:enhance>
          <input name="id" type="hidden" value={movie._id} />
          <button class="btn btn-success">Add to watchlist</button>
        </form>
      {/if}
    </div>
  </div>
</div>

<style>
  .movie-card {
    border: 1px solid #555;
    height: 100%;
    background-color: #444;
    color: white;
  }
  .details {
    padding: 0.5em;
  }
  .title {
    font-weight: bold;
  }
</style>
