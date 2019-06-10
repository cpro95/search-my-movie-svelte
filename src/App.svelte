<script>
  import Router from "svelte-spa-router";
  import Home from "./routes/Home.svelte";
  import About from "./routes/About.svelte";
  import Detail from './routes/Detail.svelte';

  const routes = {
    "/": Home,
    "/about": About,
    "/detail/:id": Detail,
    "*": Home
  };
</script>

<style>

</style>

<Router {routes} />
