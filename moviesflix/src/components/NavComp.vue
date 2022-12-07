<script>
import GeneroApi from "../api/genero";
const generoApi = new GeneroApi();

export default {
  data() {
    return {
      generos: [],
      generosTV: [],
    };
  },
  async created() {
    this.generos = await generoApi.buscarTodosOsGeneros();
    this.generosTV = await generoApi.buscarTodosOsGenerosTV();
  },
  methods: {
    buscarFilmeDir(id) {
      return `/filmes/${id}`;
    },
    buscarSerieDir(id) {
      return `/series/${id}`;
    },
  },
};
</script>
<template>
  <nav class="navbar navbar-expand-lg navbar navbar-light" style="background-color: #e3f2fd;">
    <div class="container-fluid p-3">
      <RouterLink to="/" class="nav-brad links">MoviesFlix</RouterLink>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item dropdown">
            <RouterLink
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdown"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
              to="/"
              >Filmes</RouterLink
            >
            <ul class="dropdown-menu" aria-labelledby="navbarScrollingDropdown">
              <li v-for="genero of generos" :key="genero.id">
                <router-link
                  class="dropdown-item"
                  :to="buscarFilmeDir(genero.id)"
                  >{{ genero.name }}</router-link
                >
              </li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <RouterLink
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdown"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
              to="/"
              >Séries</RouterLink
            >
            <ul class="dropdown-menu" aria-labelledby="navbarScrollingDropdown">
              <li v-for="genero of generosTV" :key="genero.id">
                <router-link
                  class="dropdown-item"
                  :to="buscarSerieDir(genero.id)"
                  >{{ genero.name }}</router-link
                >
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<style scoped>
input {
  background-color: rgb(56, 55, 55);
  color: black;
  border: black;
}

button {
  background-color: rgb(56, 55, 55);
  color:rgb(223, 243, 255);
  border:rgb(223, 243, 255);
}

.nav-brad {
  color: rgb(56, 55, 55);
  font-family: Georgia, "Times New Roman", Times, serif;
  margin: 0px 30px 18px 30px;
  text-decoration: none;
  text-align: center;
  font-weight: bold;
}
.nav-link {
  color: rgb(34, 33, 33);
  margin: 0px 0px 19px 0px;
}
::placeholder {
  color: rgb(223, 243, 255);
}
</style>
