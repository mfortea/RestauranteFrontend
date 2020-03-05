<script>
  export let busqueda;
</script>

<style>
  input {
    border-radius: 8px;
    background-color: #d3d3d3;
    transition-duration: 0.2s;
    border-color: rgb(160, 160, 160);
    border-style: solid;
    font-size: 18px;
    font-weight: bold;
  }

  input:hover {
    background-color: #e6e6e6;
  }

  @media screen and (max-width: 700px) {
    input {
      text-align: center;
      margin: 0 auto;
      width: -webkit-fill-available;
    }
  }
</style>

<label>
  <input bind:value={busqueda} placeholder="🔎 Buscar" type="search" />
</label>
