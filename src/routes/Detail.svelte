<script>
  import Navbar from "../components/Navbar.svelte";
  export let params = {};
</script>

<Navbar />
<p>detail page</p>
 {params.id}
