<div class="food-neon">
  <div class="panel">
    <div class="structure">
      <div />
      <div />
      <div />
      <div />
    </div>
    <img class="hot-dog" src="hot-dog.png" alt="" />
    <div class="title">FOOD</div>
    <div class="phrase">
      <span>To</span> take away
    </div>
  </div>
</div>

<style lang="scss">
  @mixin neon($color) {
    color: #fff;
    text-shadow: 0 0 3px #fff, 0 0 5px $color, 0 0 15px $color, 0 0 30px $color;
  }

  .food-neon {
    --structure-width: 2px;
    --structure-color: #634a3b;
    position: relative;
    box-sizing: border-box;
    width: 100%;
    height: 100%;
    transform-origin: bottom;
    transform: rotateX(-90deg);
    display: flex;
    flex-direction: column;
    border-left: var(--structure-width) solid var(--structure-color);
    border-right: var(--structure-width) solid var(--structure-color);
  }

  .hot-dog {
    position: absolute;
    width: 146px;
    top: -28px;
    right: -49px;
    filter: saturate(0.5);
  }

  .panel {
    height: 70px;
    border: var(--structure-width) solid var(--structure-color);
  }

  .structure {
    position: absolute;
    z-index: -1;
    width: 100%;
    display: flex;

    & > div {
      position: relative;
      width: 25%;
      aspect-ratio: 1;
      border-left: var(--structure-width) solid var(--structure-color);
      overflow: hidden;

      &::before,
      &::after {
        content: "";
        display: block;
        width: var(--structure-width);
        height: 150%;
        position: absolute;
        top: -25%;
        left: calc(50% - var(--structure-width) * 0.5);
        background-color: var(--structure-color);
      }

      &::before {
        transform: rotate(45deg);
      }

      &::after {
        transform: rotate(-45deg);
      }
    }
  }

  .title {
    font-size: 4rem;
    font-family: "Comfortaa", cursive;
    @include neon(rgb(254, 55, 33));
  }

  .phrase {
    position: absolute;
    top: 43px;
    left: 66px;
    font-family: "Dancing Script", cursive;
    font-size: 2.5rem;
    transform: skewY(-10deg);
    @include neon(#0fa);

    span {
      color: rgb(75, 75, 75);
      animation: flicker 1.5s infinite alternate;
    }
  }

  @keyframes flicker {
    0%,
    18%,
    22%,
    25%,
    53%,
    57%,
    100% {
      text-shadow: none;
      color: rgb(75, 75, 75);
    }

    20%,
    24%,
    55% {
      text-shadow: inherit;
      color: #fff;
    }
  }
</style>
