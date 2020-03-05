<script>
  import { Route } from "svelte-routing";
  import Inicio from "./Inicio.svelte";
  import Platos from "./Platos.svelte";
  import Cocineros from "./Cocineros.svelte";
</script>

<style>
  main {
    padding: 30px;
  }

  @media screen and (max-width: 700px) {
    main {
      padding: 0px;
    }
  }
</style>

<main>
  <Route path="/" component={Inicio} />
  <Route path="/platos" component={Platos} />
  <Route path="/cocineros" component={Cocineros} />
</main>
