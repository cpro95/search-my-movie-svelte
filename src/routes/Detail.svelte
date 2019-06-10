<script>
  import Navbar from "../components/Navbar.svelte";
  import { movie_store } from "../stores.js";


  // when movie_store is not available
  // which means params.id is only key to filter movie

  // import moviesDB from "../movies-data.json";
  // export let params = {};
  // var filteredMovie = moviesDB.filter(movie => {
    // if (parseInt(movie.idMovie) === parseInt(params.id)) return true;
    // else return false;
  // });
  // console.log(filteredMovie);



  // using svelte store
  var movie=$movie_store;
</script>

<Navbar />
<p>detail page</p>
 <!-- {params.id} -->
{movie.c00}
{movie.c01}
{movie.c03}
