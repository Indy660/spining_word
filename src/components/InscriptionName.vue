<template>
  <div class="name">{{ inscription }}</div>
</template>

<script>
export default {
  name: "InscriptionName",
  data() {
    return {
      inscription: 'CSS'
    }
  }
}
</script>

<style scoped>
.name {
  font-family: 'Fredoka One', cursive;
  position: absolute;
  top: 50%;
  left: 50%;
  animation: color 3s infinite linear;
  text-shadow: 0 0 10px #000a;
  transition: all 0.5s;
}
</style>