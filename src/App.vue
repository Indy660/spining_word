<template>
  <div class="main">
    <template v-for="item in 225" :key="item">
      <CellComponent/>
    </template>

    <div class="content">
      <template v-for="item in 10" :key="item">
        <InscriptionName/>
      </template>
    </div>
  </div>
</template>

<script>
import CellComponent from "@/components/CellComponent";
import InscriptionName from "@/components/InscriptionName";
export default {
  name: 'App',
  components: {
    CellComponent,
    InscriptionName,
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&display=swap');

*, *::before, *::after {
  padding: 0;
  margin: 0 auto;
  box-sizing: border-box;
}

.main {
  background-color: black;
  height: 100vh;
  display: grid;
  grid-template: repeat(15, 1fr) / repeat(15, 1fr);
  overflow: hidden;
}

@for $i from 0 to 15 {
  .cell:nth-child(15n + #{$i + 1}):hover ~ .content {
    //передвижение надписи по оси х за мышкой
    --positionX: #{$i};
  }
  .cell:nth-child(n + #{15 * $i + 1}):nth-child(-n + #{15 * ($i + 1)}):hover ~ .content {
    //передвижение надписи по оси у за мышкой
    --positionY: #{$i};
  }
}

.content {
  //начальное направление текста
  --positionX: 7;
  --positionY: 7;

  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.css {
  @for $i from 0 to 10 {
    &:nth-child(#{$i + 1}) {
      font-size: #{100 + $i * 10}px;
      animation-delay: #{$i * -0.3}s;
      opacity: #{0.1 + $i * 0.1};
      transform:
          translateX(calc(-50% - (var(--positionX) - 7) * #{(7 - $i) * 3px}))
          translateY(calc(-50% - (var(--positionY) - 7) * #{(7 - $i) * 3px}))
          rotateX(calc(0deg - (var(--positionY) - 7) * 5deg))
          rotateY(calc((var(--positionX) - 7) * 5deg));
    }
  }

  // изменение цвета
  @keyframes color {
    @for $c from 0 through 10 {
      #{$c * 10%} { color: hsl(36 * $c, 75%, 75%); }
    }
  }
}
</style>
