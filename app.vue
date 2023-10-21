<script setup>
const user = useSupabaseUser()
</script>

<template>
  <div class="container">
    <Account v-if="user" />
    <Auth v-else />
  </div>
</template>

<style scoped>

*{
    box-sizing: border-box;
    margin: 0;
}
.container{
  box-sizing: border-box;
  margin: 0;
}
</style>
