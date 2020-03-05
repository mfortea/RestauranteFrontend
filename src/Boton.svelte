<script>
  import { onMount, getContext } from "svelte";
  import { jsonData } from "./store.js";
  export let tipo = "insertar";
  export let coleccion = "platos";
  export let documento = {};

  let handler = () => {};
  let clases = "";
  let url = "";
  const URL = getContext("URL");
  onMount(() => {
    switch (tipo) {
      case "insertar":
        handler = insertar;
        clases = "btn btn-insertar";
        break;
      case "modificar":
        handler = modificar;
        clases = "btn btn-modificar";
        break;
      case "eliminar":
        handler = eliminar;
        clases = "btn btn-eliminar";
        break;
      default:
    }
    switch (coleccion) {
      case "platos":
        url = URL.platos;
        break;
      case "cocineros":
        url = URL.cocineros;
        break;
      default:
    }
  });
  function insertar() {
    if (
      Object.keys(documento).length > 1 &&
      Object.values(documento).every(x => x !== undefined && x != "")
    ) {
      fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(documento)
      })
        .then(res => res.json())
        .then(data => {
          $jsonData = [...$jsonData, data];
          ok();
        })
        .catch(err => ko());
    }
  }
  function modificar() {
    fetch(url + documento.nombre, {
      method: "PUT",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(documento)
    })
      .then(res => res.json())
      .then(data => ok())
      .catch(err => ko());
  }
  function eliminar() {
    fetch(url + documento.nombre, { method: "DELETE" })
      .then(res => res.json())
      .then(data => {
        $jsonData = $jsonData.filter(x => x._id !== data._id);
        ok();
      })
      .catch(err => ko());
  }
  let ok = () => {
    OK.style.display = "block";
    setTimeout(() => (OK.style.display = "none"), 1500);
  };
  let ko = () => {
    KO.style.display = "block";
    setTimeout(() => (KO.style.display = "none"), 1500);
  };
</script>

<style>
  .btn {
    font-weight: bold;
    padding: 10px;
    cursor: pointer;
    border-radius: 8px;
    transition: all 0.2s linear;
    border-style: none;
  }

  /* Botón para insertar */
  .btn-insertar {
    color: #094101;
    background-color: rgb(8, 180, 8);
  }
  .btn-insertar::after {
    content: " Insertar";
  }
  .btn-insertar:hover {
    background: #03d11e;
  }

  /* Botón para modificar */
  .btn-modificar {
    color: #000000;
    background-color: rgb(255, 120, 1);
  }

  .btn-modificar::after {
    content: " Modificar";
  }
  .btn-modificar:hover {
    background: #ff9900;
  }

  /* Botón para eliminar */
  .btn-eliminar {
    color: #000000;
    background-color: rgb(223, 14, 14);
  }
  .btn-eliminar::after {
    content: " Eliminar";
  }
  .btn-eliminar:hover {
    background: #ff0800;
  }

</style>

<button class={clases} on:click={handler} />
