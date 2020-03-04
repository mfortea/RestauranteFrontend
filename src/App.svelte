<script>
  import { setContext } from "svelte";
  import { Router } from "svelte-routing";
  import Menu from "./Menu.svelte";
  import Contenido from "./Contenido.svelte";
  import Pie from "./Pie.svelte";

  const URL = {
    platos: "https://restaurantebackend.herokuapp.com/api/platos/",
    cocineros: "https://restaurantebackend.herokuapp.com/api/cocineros/"
  };

  setContext("URL", URL);
</script>

<Router>
  <Menu />
  <Contenido />
</Router>
<Pie />
