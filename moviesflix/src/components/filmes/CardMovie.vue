<script>
export default {
  props: {
    filme: {
      type: Object,
    },
  },
  methods: {
    mostrarFilme() {},
  },
};
</script>
<template>
  <div @click="mostrarFilme" class="card m-2">
    <img :src="filme.imagem" class="card-img-top" alt="" />
    {{ filme.autor }}
  </div>
</template>
<style scoped>
.card-img-top{
  width: 160px;
  margin: 0px 0px 0px 50px;
}
</style>
