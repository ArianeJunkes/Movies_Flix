<script>
import CardMovie from "../components/filmes/CardMovie.vue";
import RodapeComp from "../components/RodapeComp.vue";
import FilmeApi from "@/api/filmes";
const filmeApi = new FilmeApi();

export default {
  props: ["id"],
  components: { CardMovie, RodapeComp },
  data() {
    return {
      movies: [],
    };
  },
  async created() {
    this.movies = await filmeApi.buscarTodosOsFilmesPorGenero(this.id);
  },
  methods: {
    getImageUrl(poster_path) {
      return `https://image.tmdb.org/t/p/w500/${poster_path}`;
    },
  },
  watch: {
    async id() {
      this.movies = await filmeApi.buscarTodosOsFilmesPorGenero(this.id);
    },
  },
};
</script>
<template>
  <!-- <div class="container"> -->
  <div class="row">
    <div class="col mt-14" v-for="movie of movies" :key="movie.id">
      <h3>{{ movie.title }}</h3>
      <p class="nota">{{ movie.vote_average }}</p>
      <img :src="getImageUrl(movie.poster_path)" alt="" />
    </div>
  </div>
  <!-- </div> -->
  <RodapeComp></RodapeComp>
</template>

<style scooped>
.row {
  background-color: rgb(56, 55, 55);
}

h3 {
  color: rgb(223, 243, 255);
  font-size: 30px;
  font-family: "Times New Roman", Times, serif;
  margin: 0px 20px 0px 100px;
}

img{
  margin:0px 0px 0px 100px;

}
.nota {
  background-color: rgb(223, 243, 255);
  border: 1px rgb(56, 55, 55) solid;
  border-radius: 145px;
  margin: 10px 20px 2px 100px;
  padding: 4px;
  width: 8%;
  color: rgb(56, 55, 55);
  font-size: 17px;
  font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
  text-align: center;
}
</style>
