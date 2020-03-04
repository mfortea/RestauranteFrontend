<script>
  export let plato = {};
</script>

<style>
  .card {
    background-color: #a0a0a0;
    border-radius: 5px;
    border-color: rgb(181, 119, 3);
    border-width: 3px;
    border-style: solid;
    padding: 25px;
    margin: 30px;
    transition-duration: 0.5s;
    width: 300px;
    box-shadow: 0px 0px 68px -21px rgba(0,0,0,0.75);
    transition-duration: 0.2s;
  }

  .card:hover {
      box-shadow: 0px 35px 90px -14px rgba(0,0,0,0.75);

  }

  input {
    background-color: #d3d3d3;
    border-color: rgb(91, 91, 91);
    border-radius: 5px;
    font-weight: bold;
  }

  input[type="number"] {
    text-align: left;
    width: 90px;
  }
  input:focus {
    background-color: rgb(189, 189, 189);
  }

  input:required:invalid,
  input:focus:invalid {
    background-color: rgb(255, 1, 39);
  }
</style>

<div class="card">
  <slot />
  <br>
  <input
    bind:value={plato.nombre}
    placeholder="Nombre del plato"
    class="title" />
    <br>
  <input bind:value={plato.tipo} placeholder="Tipo de plato" class="title" />
  <br />
  <input
    bind:value={plato.minutosElaboracion}
    type="number"
    min="1"
    max="9999"
    placeholder="Tiempo" />
  minuto/s
  <br />
  <input
    placeholder="Precio"
    type="number"
    min="0"
    max="9999.99"
    step=".01"
    bind:value={plato.precio} />
  €
</div>
