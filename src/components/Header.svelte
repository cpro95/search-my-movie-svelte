<script>
  import Navbar from "./Navbar.svelte";
  import Logo from "./logo.svelte";
</script>

<style>
  .herostyle {
    opacity: 0.95;
    background: #499bea;
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr=#499bea, endColorstr=#798eea, GradientType=1);
  }
</style>

<section>
  <Navbar />
  <div class="jumbotron jumbotron-fluid herostyle">
    <div class="container">
      <Logo />
      <h1 class="display-4 text-white">Search My Movie</h1>
      <p class="lead text-white">out of Kodi DB</p>
    </div>
  </div>
</section>
