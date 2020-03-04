<script>
  export let busqueda;
</script>

<style>
  input{
    border-radius: 8px;
  }
</style>

<label>
  Buscar &nbsp;
  <input bind:value={busqueda} type="search" />
</label>
