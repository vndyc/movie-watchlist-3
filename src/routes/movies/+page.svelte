<script>
  import MovieCard from "$lib/components/MovieCard.svelte";
  let { data } = $props();

  let filterByWatchlist = $state(false);
</script>

<p><i>Daten und Bilder generiert mit ChatGPT und DALL-E</i></p>
<div>
  <a href="/movies/create" class="btn btn-primary">Add New Movie</a>
</div>
<div class="form-check mt-3">
  <input
    bind:checked={filterByWatchlist}
    class="form-check-input"
    type="checkbox"
    value=""
    id="checkDefault"
  />
  <label class="form-check-label" for="checkDefault">
    Show only movies on watchlist
  </label>
</div>
<div class="row mt-3">
  {#each data.movies as movie}
    {#if !filterByWatchlist || (filterByWatchlist && movie.watchlist)}
      <div class="col-sm-6 col-md-4 col-lg-3 mb-2 gx-2">
        <MovieCard {movie}></MovieCard>
      </div>
    {/if}
  {/each}
</div>
