<script>
  import { Link } from "svelte-routing";
</script>

<style>
  nav {
    background-color: rgb(65, 65, 65);
    border-radius: 10px;
    padding: 8px;
    box-shadow: -5px 5px 30px 0px rgba(0, 0, 0, 0.75);
  }
  img {
    float: left;
    margin-left: 26px;
    padding: 5px;
  }

  p {
    display: inline;
    color: white;
    margin-left: 10px;
    font-size: 22px;
  }

  ul {
    list-style-type: none;
    display: inline-flex;
  }

  .elemento-menu {
    font-size: 18px;
    margin-left: 10px;
    background-color: rgb(101, 101, 101);
    padding: 8px;
    border-radius: 5px;
    transition-duration: 0.2s;
    transition-timing-function: linear;
    width: 100px;
    text-align: center;
  }

  .elemento-menu:hover {
    background-color: rgb(14, 14, 14);
    transition-duration: 0.2s;
    transition-timing-function: linear;
  }

  .texto-menu {
    color: rgb(255, 255, 255);
  }
</style>

<div>
  <nav>

    <img alt="Logo" src="favicon.png" width="50px" />

    <p>
      <strong>Restaurante</strong>
      Frontend
    </p>

    <ul>

      <Link to="/">
        <li class="elemento-menu">
          <span class="texto-menu">Inicio</span>
        </li>
      </Link>

      <Link to="/platos">
        <li class="elemento-menu">
          <span class="texto-menu">Platos</span>
        </li>
      </Link>

      <Link to="/cocineros">
        <li class="elemento-menu">
          <span class="texto-menu">Cocineros</span>
        </li>
      </Link>

    </ul>

  </nav>
</div>
