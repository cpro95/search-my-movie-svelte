<script>
  import { link } from "svelte-spa-router";
</script>

<style>

</style>

<ul class="nav">
  <li class="nav-item">
    <a class="nav-link" href="/" use:link>Home</a>
  </li>
  <li class="nav-item">
      <a class="nav-link" href="/about" use:link>About</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="http://github.com/cpro95/search-my-movie">
      Github
    </a>
  </li>
</ul>
