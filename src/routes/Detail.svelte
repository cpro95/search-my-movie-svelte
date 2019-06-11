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
  var movie = $movie_store;

  var youtube_link;
  var youtube_embed_link;
  var imdb_link;
  var link_str;
  var target_str = "" + movie.c19;

  link_str = target_str.substr(
    target_str.indexOf("videoid") + 8,
    target_str.length
  );
  youtube_link = `https://www.youtube.com/watch?v=${link_str}`;
  youtube_embed_link = `https://www.youtube.com/embed/${link_str}`;
  imdb_link = `http://www.imdb.com/title/${movie.uniqueid_value}`;

  var title = "";

  if (movie.c00 !== movie.c16) {
    title = movie.c00 + " (" + movie.c16 + ")";
  } else {
    title = movie.c00;
  }
</script>

<Navbar />
<div
  class="container-fluid"
  style=" background: black; background-repeat: no-repeat; background-size:
  cover; background-image: {'url(' + movie.c20 + ')'}">
  <div class="text-light">
    <img
      class="img-fluid"
      style="margin-top: 20px;margin-bottom: 20px"
      src={movie.c08}
      alt="Poster" />
    <div class="bg-dark mb-2 p-3" style="opacity: 0.9;">
      <h1 class="mb-3">{title}</h1>
      <h4 class="mb-3">{movie.c03}</h4>
      <span class="badge badge-light">
        Rating: {parseFloat(movie.rating).toFixed(1)}
      </span>
       {' / '}
      <span class="badge badge-primary">premiered: {movie.premiered} </span>
      <p class="lead mt-3 mb-3">{movie.c01}</p>

      <div class="embed-responsive embed-responsive-16by9 my-3">
        <iframe
          class="embed-responsive-item"
          src={youtube_embed_link}
          frameborder="0"
          allow="accelerometer; autoplay; encrypted-media; gyroscope;
          picture-in-picture"
          allowfullscreen
          title={movie.c00} />
      </div>

      <div class="mb-3">
        <a class="btn btn-light btn-sm" target="blank" href={youtube_link}>
          View Trailer
        </a>
         {' '}
        <a class="btn btn-primary btn-sm" target="blank" href={imdb_link}>
          Learn More 
        </a>
      </div>
      <p class="text-success">
        <span class="badge badge-warning">Location</span>
         {movie.strPath}
      </p>
    </div>
  </div>

</div>
