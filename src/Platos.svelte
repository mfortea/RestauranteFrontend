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
</style>

<h1>Platos</h1>
<Buscar bind:busqueda />

<div>
  <Plato bind:plato>
  <h2>Insertar nuevos platos</h2>
  <Boton documento={plato} tipo="insertar" coleccion="platos" />
  </Plato>
</div>

<br/>

<h2>Lista de platos</h2>
<div class="container">
  {#each datos as plato}
    <Plato {plato}>
      <div style="text-align: left">
        <h1>{plato.nombre}</h1>
        <h2>{plato.tipo} | {plato.precio}€</h2>
        <p>Preparado en {plato.minutosElaboracion} minutos</p>
          <Boton documento={plato} tipo="modificar" coleccion="platos" />
          <Boton documento={plato} tipo="eliminar" coleccion="platos" />
      </div>
    </Plato>
  {/each}
</div>
