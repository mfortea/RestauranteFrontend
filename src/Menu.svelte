<script>
  import { Link } from "svelte-routing";
</script>

<style>
  nav {
    background-color: rgb(71, 71, 71);
    border-radius: 2px;
    padding: 8px;
    position: sticky;
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
    background-color: rgb(175, 85, 0);
    transition-duration: 0.2s;
    transition-timing-function: linear;
  }

  .texto-menu {
    color: rgb(255, 255, 255);
  }

  @media screen and (max-width: 700px) {
    img {
      margin: 0 auto;
    }

    p {
      text-align: center;
      display: block;
    }

    ul {
      display: block;
      padding: 0px;
    }

    .elemento-menu {
      width: auto;
      border-radius: 0px;
      border-color: grey;
      border-style: solid;
      border-width: 2px;
    }
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
