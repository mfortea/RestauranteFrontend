<script>
  import { onMount, getContext } from "svelte";
  import { jsonData } from "./store.js";

  import Buscar from "./Buscar.svelte";
  import Plato from "./Plato.svelte";
  import Boton from "./Boton.svelte";

  const URL = getContext("URL");

  let busqueda = "";
  let plato = {};

  onMount(async () => {
    const response = await fetch(URL.platos);
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

  span{
    margin-left: 60px;
  }

</style>

<h1>
  <img alt="Icono platos" width="50px" src="/platos.png" />
  <span>Platos</span>
</h1>
<Buscar bind:busqueda />

<br />

<h2>Añadir un nuevo plato</h2>
<div>
  <Plato bind:plato>
    <br />
    <br />
    <Boton documento={plato} tipo="insertar" coleccion="platos" />
  </Plato>
</div>

<br />

<h2>Lista de platos</h2>
<div class="container">
  {#each datos as plato}
    <Plato {plato}>
      <div style="text-align: left">
        <Boton documento={plato} tipo="modificar" coleccion="platos" />
        <Boton documento={plato} tipo="eliminar" coleccion="platos" />
      </div>
    </Plato>
  {/each}
</div>
