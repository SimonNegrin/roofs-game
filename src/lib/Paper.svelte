<script>

  export let size = [5, 7]
  export let pos = [5, 7]
  export let rot = 0

</script>

<div
  class="paper"
  style="
    width: {size[0]}px;
    height: {size[1]}px;
    left: {pos[0]}px;
    top: {pos[1]}px;
    transform: rotateZ({rot}deg);
  " />

<style>
  .paper {
    position: absolute;
    background-color: #f3f3e9;
  }
</style>
