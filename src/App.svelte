<script>
  import Bike from './lib/Bike.svelte'
  import Building from './lib/Building.svelte'
  import FoodNeon from './lib/FoodNeon.svelte'
  import Lader from './lib/Lader.svelte'
  import Paper from './lib/Paper.svelte'
  import Stairs from './lib/Stairs.svelte'

  let sceneX = 240

  const onWheel = (e) => {
    sceneX -= e.deltaY
  }

</script>

<div class="game" on:wheel|preventDefault={onWheel}>
  <div class="scene" style="--scene-x: {sceneX}px">
    <Building width={300} height={400} x={50}>
      <FoodNeon />
    </Building>
    <Building width={200} height={250} x={350} z={-10}>
      <Lader rot={-90} pos={[-5, 80]} />
      <Stairs steps={5} rot={90} left="100%" top="10%" />
      <Paper size={[10, 15]} rot={60} />
      <Paper size={[10, 15]} pos={[15, 12]} rot={60} />
      <Paper size={[10, 15]} pos={[50, 22]} rot={13} />
      <Paper size={[10, 15]} pos={[55, 27]} rot={145} />
      <Paper size={[10, 15]} pos={[75, 76]} rot={43} />
      <!-- <Bike /> -->
    </Building>
    <Building width={220} height={300} x={550}>
      <Stairs steps={12} left="85%" top="20%" />
    </Building>
    <Building width={220} height={420} x={770} z={10}>
      <Lader steps={6} rot={95} pos={[95, 80]} />
    </Building>
    <Building width={320} height={500} x={990} />
    <Building width={220} height={270} x={1310} z={-10} />
    <Building width={140} height={210} x={1530} z={-15} />
    <Building width={200} height={410} x={1670} />
    <Building width={230} height={510} x={1870} z={10} />
  </div>
</div>

<style lang="scss">

  .game {
    width: 100vw;
    height: 100vh;
    background-color: #251d1a;
    position: relative;
    perspective: 700px;
    perspective-origin: 61% 58%;
    overflow: hidden;
    transform-style: preserve-3d;
  }

  .scene {
    height: 100%;
    transform-style: preserve-3d;
    transform: rotateX(-20deg) rotateY(15deg) translateZ(100px) translateX(var(--scene-x));
  }

</style>
