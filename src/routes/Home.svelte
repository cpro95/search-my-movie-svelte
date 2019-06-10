<script>
  import Header from "../components/Header.svelte";
  import { link } from "svelte-spa-router";
  import movies from "../movies-data.json";

  function handleClick() {

  }
</script>

<style>
  table th a, table td a{
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
      autofocus />
  </div>
  <h2 class="h5">Search count : {movies.length}</h2>

  <a href="/detail/1" use:link>id : 1</a>
  <table class="table table-striped">
    <thead class="thead-dark">
      <tr>
        <th scope="col">No</th>
        <th scope="col">Name</th>
        <th scope="col">Rating / Premiered</th>
      </tr>
    </thead>
    <tbody>
      {#each movies as movie}
        <tr key={movie.idMovie}>
          <th scope="row">
            <a
              style="display:block;width:100%;height:100%"
              href={'/detail/' + movie.idMovie}
              use:link>
              {movie.idMovie}
            </a>
          </th>
          <td>
            <a href={'/detail/' + movie.idMovie} use:link> {movie.c00} </a>
          </td>
          <td>
            <a href={'/detail/' + movie.idMovie} use:link>
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
