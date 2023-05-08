<div class="bike">
  <div class="wheel back">
    <div class="frame"></div>
  </div>
  <div class="wheel front">
    <div class="fork"></div>
  </div>
</div>

<style lang="scss">

  .bike {
    --bike-color: rgb(110, 79, 36);
    position: absolute;
    width: 100px;
    aspect-ratio: 1.5;
    left: 14px;
    top: 40px;
    transform-origin: left bottom;
    transform: rotateX(264deg) rotateY(96deg);
  }

  .wheel {
    position: absolute;
    bottom: 0;
    width: 35%;
    aspect-ratio: 1;
    border: 3px solid #000;
    border-radius: 50%;
    transform-style: preserve-3d;

    &.back {
      left: 0;
    }

    &.front {
      right: 0;
    }
  }

  .frame {
    position: absolute;
    width: 70%;
    height: 60%;
    bottom: 47%;
    left: 47%;
    border: 3px solid var(--bike-color);
    transform: skewX(-35deg);
    transform-origin: left bottom;
    transform-style: preserve-3d;

    &::before {
      content: '';
      display: block;
      width: 3px;
      height: 150%;
      background-color: var(--bike-color);
      transform-origin: top center;
      transform: rotateZ(-50deg);
    }
  }

  .fork {
    position: absolute;
    width: 3px;
    height: 100%;
    bottom: 47%;
    left: 47%;
    background-color: var(--bike-color);
    transform: rotateZ(-25deg);
    transform-origin: bottom;
    transform-style: preserve-3d;
  }

</style>