<script>
export default {
  props: {
    serie: {
      type: Object,
    },
  },
  methods: {
    mostrarSerie() {},
  },
};
</script>

<template>
  <div @click="mostrarSerie" class="card m-2">
    <img :src="serie.imagem" class="card-img-top" alt="" />
    {{ serie.autor }}
  </div>
</template>
<style scoped>
.card-img-top{
  width: 160px;
  margin: 0px 0px 0px 50px;
}
</style>
