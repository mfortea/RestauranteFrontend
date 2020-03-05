<script>
  import { onMount, getContext } from "svelte";
  import { jsonData } from "./store.js";

  import Buscar from "./Buscar.svelte";
  import Cocinero from "./Cocinero.svelte";
  import Boton from "./Boton.svelte";

  const URL = getContext("URL");

  let busqueda = "";
  let cocinero = {};

  onMount(async () => {
    const response = await fetch(URL.cocineros);
    const data = await response.json();
    $jsonData = data;
  });

  $: regex = new RegExp(busqueda, "i");
  $: datos = busqueda
    ? $jsonData.filter(item => regex.test(item.nombre))
    : $jsonData;
</script>

<style>
  .container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: left;
    flex-wrap: wrap;
  }

  img {
    position: absolute;
  }

  span {
    margin-left: 60px;
  }

  @media screen and (max-width: 700px) {

    h2 {
      text-align: center;
    }
    .container {
      display: block;
    }
  }
</style>

<h1>
  <img alt="Icono platos" width="50px" src="/gorro.png" />
  <span>Cocineros</span>
</h1>
<Buscar bind:busqueda />

<br />

<h2>Añadir un nuevo cocinero</h2>
<div>
  <Cocinero bind:cocinero>
    <br />
    <br />
    <Boton documento={cocinero} tipo="insertar" coleccion="cocineros" />
  </Cocinero>
</div>

<br />

<h2>Lista de cocineros</h2>
<div class="container">
  {#each datos as cocinero}
    <Cocinero {cocinero}>
      <div style="text-align: left">
        <Boton documento={cocinero} tipo="modificar" coleccion="cocineros" />
        <Boton documento={cocinero} tipo="eliminar" coleccion="cocineros" />
      </div>
    </Cocinero>
  {/each}
</div>
