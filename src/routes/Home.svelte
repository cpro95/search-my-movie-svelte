<script>
  import Header from "../components/Header.svelte";
  import { onDestroy } from "svelte";
  import { link } from "svelte-spa-router";
  import moviesDB from "../movies-data.json";
  import { movie_store } from "../stores.js";

  let movie_store_value;

  const unsubscribe = movie_store.subscribe(value => {
    movie_store_value = value;
  });

  function handleClick(movie) {
    movie_store.update(n => (n = movie));
  }

  onDestroy(unsubscribe);

  let movies = moviesDB;
  let searchKeyword = "";

  function handleChange(e) {
    var filteredMovies = moviesDB.filter(movie => {
      // console.log(movie.c00.indexOf(searchKeyword));
      if (movie.c00.toLowerCase().indexOf(e.target.value.toLowerCase()) !== -1)
        return true;
      else return false;
    });
    // when search keyword is empty, check with trim method
    if (e.target.value.trim() !== "") movies = filteredMovies;
    else movies = moviesDB;
  }
</script>

<style>
  table th a,
  table td a {
    display: block;
    width: 100%;
    height: 100%;
    text-decoration: none;
  }
</style>

<section>
  <Header />
  <div class="input-group input-group-sm mb-3">
    <input
      type="text"
      class="form-control"
      placeholder="Search Movies..."
      bind:value={searchKeyword}
      on:keyup={handleChange}
      autofocus />
  </div>
  <h2 class="h5"> Total : {movies.length}</h2>

  <table class="table table-striped">
    <thead class="thead-dark">
      <tr>
        <th scope="col">No</th>
        <th scope="col">Name</th>
        <th scope="col">Rating / Premiered</th>
      </tr>
    </thead>
    <tbody>
      {#each movies as movie (movie.idMovie)}
        <tr>
          <th scope="row">
            <a
              style="display:block;width:100%;height:100%"
              href={'/detail/' + movie.idMovie}
              use:link
              on:click={() => handleClick(movie)}>
               {movie.idMovie}
            </a>
          </th>
          <td>
            <a
              on:click={() => handleClick(movie)}
              href={'/detail/' + movie.idMovie}
              use:link>
               {movie.c00}
            </a>
          </td>
          <td>
            <a
              on:click={() => handleClick(movie)}
              href={'/detail/' + movie.idMovie}
              use:link>
              <span class="badge badge-dark">
                 {parseFloat(movie.rating).toFixed(1)}
              </span>
               {' / '}
              <span class="badge badge-secondary"> {movie.premiered} </span>
            </a>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</section>
