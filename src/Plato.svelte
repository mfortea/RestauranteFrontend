<script>
  export let plato = {};
</script>

<style>
  .card {
    border-radius: 5px;
    padding: 25px;
    margin: 15px;
    transition-duration: 0.5s;
    width: 300px;
    transition-duration: 0.2s;
    background-color: rgb(163, 162, 162);
    border-style: dotted;
    border-color: rgb(134, 134, 134);
    border-width: 4px;
    transition-duration: 0.2s;
  }

  .card:hover {
    border-style: solid;
    border-color: rgb(219, 143, 2);
    box-shadow: 0px 19px 54px -30px rgba(0, 0, 0, 0.75);
  }

  input {
    background-color: #b6b4b4;
    border-color: rgb(91, 91, 91);
    border-radius: 5px;
    font-weight: bold;
    border-style: none;
    transition-duration: 0.2s;
  }

  input:hover {
    background-color: #c2c2c2;
  }

  input:focus {
    background-color: #e6e6e6;
  }

  input[type="number"] {
    text-align: left;
    width: 90px;
  }

  input:required:invalid,
  input:focus:invalid {
    background-color: rgb(255, 1, 39);
  }

   @media screen and (max-width: 700px) {
     .card {
       width: auto;
     }
  }
</style>

<div class="card">
  <br />
  <input
    bind:value={plato.nombre}
    placeholder="Nombre del plato"
    class="title" />
  <br />
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
  <slot />
</div>
