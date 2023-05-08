<script>

  export let width = 100
  export let height = 100
  export let z = 0
  export let x = 0

</script>

<div
  class="building"
  style="--z: {z}px; width: {width}px; height: {height}px; left: {x}px;"
  >
  <div class="roof">
    <slot />
  </div>
  <div class="guard-rail"></div>
  <div class="wall wall-a"></div>
  <div class="wall wall-b"></div>
</div>

<style lang="scss">

  .building {
    --deep: 200px;
    position: absolute;
    bottom: -150px;
    transform-origin: bottom;
    transform: translateZ(var(--z));
    transform-style: preserve-3d;
    background-image: url('building_1.jpg');
    background-size: 100% auto;
  }

  .guard-rail {
    position: absolute;
    bottom: 100%;
    width: 100%;
    height: 25px;
    background-image: url('guard-rail.png');
    background-size: auto 100%;
  }

  .roof {
    width: 100%;
    height: var(--deep);
    background-color: red;
    transform-origin: bottom;
    position: absolute;
    left: 0;
    bottom: 100%;
    transform: rotateX(90deg);
    background-image: url('floor.jpg');
    background-size: cover;
    transform-style: preserve-3d;
  }

  .wall {
    position: absolute;
    top: 0;
    width: var(--deep);
    height: 100%;
    background-image: url('bricks_1.jpg');
    background-size: 100px auto;
  }

  .wall-a {
    left: 0;
    transform-origin: right;
    transform: rotateY(90deg);
    transform-origin: left;
    background-color: green;
  }
  
  .wall-b {
    right: 0;
    transform-origin: right;
    transform: rotateY(-90deg);
    transform-origin: right;
    background-color: blue;
  }

</style>
