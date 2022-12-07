<script setup>
import HeaderComp from "@/components/HeaderComp.vue";
</script>

<template>
  <HeaderComp />
  <main>
    <div class="conteudo">
      <RouterView />
    </div>
  </main>
</template>

<style scoped>
.conteudo {
  padding: 0 200px;
  background-color: rgb(223, 243, 255);
}

</style>
