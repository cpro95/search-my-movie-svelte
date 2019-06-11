<script>
  import { link } from "svelte-spa-router";
</script>

<style>

</style>

<nav class="navbar fixed-top navbar-dark bg-dark">
  <ul class="nav">
    <li class="nav-item">
      <a class="nav-link" href="/" use:link>Home</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="/about" use:link>About</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="https://github.com/cpro95/search-my-movie-svelte">
        Github
      </a>
    </li>
  </ul>
</nav>
