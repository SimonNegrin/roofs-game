<script>

  export let steps = 10
  export let rot = 0
  export let top = '0%'
  export let left = '0%'

</script>

<div
  class="stairs"
  style="
    --steps: {steps};
    --stairs-rot: {rot}deg;
    top: {top};
    left: {left};
  ">
  {#each Array(steps) as _, i}
    <div class="step" style="--i: {i}">
      <div class="step__top"></div>
      <div class="step__left"></div>
      <div class="step__right"></div>
    </div>
  {/each}
</div>

<style lang="scss">

  .stairs {
    --step-height: 10px;
    --stairs-height: calc(var(--step-height) * var(--steps));
    position: absolute;
    width: 60px;
    height: var(--stairs-height);
    transform-style: preserve-3d;
    transform: rotateZ(var(--stairs-rot));
    transform-origin: top left;
  }

  .step {
    --step-deep: calc(var(--stairs-height) - (var(--step-height) * var(--i)));
    position: absolute;
    width: 100%;
    height: var(--step-height);
    left: 0;
    bottom: calc(var(--step-height) * var(--i));
    transform-origin: bottom;
    transform: rotateX(-90deg) translateY(calc(var(--step-height) * var(--i) * -1));
    transform-style: preserve-3d;

    &::before {
      content: '';
      display: block;
      width: 100%;
      height: 100%;
      background-color: chartreuse;
      background-image: url('floor.jpg');
      background-position: calc(15px * var(--i)) 0;
      filter: brightness(0.5);
    }
  }

  .step__left,
  .step__right {
    position: absolute;
    top: 0;
    height: 100%;
    width: var(--step-deep);
    background-image: url('bricks_1.jpg');
    background-size: 100px auto;
    background-position: calc(10px * var(--i)) 0;
    filter: brightness(0.7);
  }

  .step__left {
    left: 0;
    background-color: crimson;
    transform-origin: left;
    transform: rotateY(90deg);
  }
  
  .step__right {
    right: 0;
    background-color: cadetblue;
    transform-origin: right;
    transform: rotateY(-90deg);
  }

  .step__top {
    position: absolute;
    bottom: 100%;
    left: 0;
    background-color: blue;
    background-image: url('floor.jpg');
    background-position: calc(10px * var(--i)) 0;
    width: 100%;
    height: var(--step-deep);
    transform-origin: bottom;
    transform: rotateX(90deg);
  }

</style>