<script>

  export let steps = 10
  export let rot = 0
  export let pos = [0, 0]

</script>

<div
  class="lader"
  style="
    transform: rotateZ({rot}deg);
    left: {pos[0]}%;
    top: {pos[1]}%;
  ">
  {#each Array(steps) as _, i}
    <div class="back" style="--i: {i};"></div>
    <div class="step" style="--i: {i};"></div>
  {/each}
</div>

<style lang="scss">
  .lader {
    --lader-step-height: 15px;
    --lader-line-width: 2px;
    position: relative;
    width: 20px;
    height: 5px;
    transform-style: preserve-3d;
    transform-origin: top center;
  }
  .back,
  .step {
    position: absolute;
    left: 0;
    width: 100%;
    height: 15px;
    box-sizing: border-box;
    border: var(--lader-line-width) solid #000;
    border-bottom: none;
    transform-origin: bottom;
    transform: rotateX(-90deg) translateY(calc(var(--lader-step-height) * var(--i) * -1));
  }

  .back {
    bottom: 100%;
    filter: blur(3px);
  }
  .step {
    bottom: 0;
    transform-style: preserve-3d;

    &::before,
    &::after {
      content: '';
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      width: 1.5px;
      height: 100%;
      background-color: #000;
      transform: rotateY(90deg);
    }

    &::after {
      left: 100%;
    }
  }
</style>
