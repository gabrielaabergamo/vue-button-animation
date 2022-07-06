<template>
  <section>
    <div
      :class="{
        polygonGrowPink: hoverPinkButton,
        polygonGrowPurple: hoverPurpleButton,
        polygonRetractPink: hoverOutPinkButton,
        polygonRetractPurple: hoverOutPurpleButton,
      }"
      class="polygon"
    ></div>

    <div class="title">
      <h1 class="title-text">
        <span class="title-text__highlight"
          >Lorem ipsum dolor sit amet</span
        >
      </h1>
    </div>

    <div class="buttons">
      <ButtonDefault 
        @mouseover="controllerPinkButtonMouseover"
        @mouseleave="controllerPinkButtonMouseleave"
        :isPink="1"
        />
      <ButtonDefault 
        @mouseover="controllerPurpleButtonMouseover"
        @mouseleave="controllerPurpleButtonMouseleave"
        :isPink="0"
       />
    </div>
  </section>
</template>

<script>
import ButtonDefault from '../components/Button.vue';

export default {
  name: "AnimationPage",
  components:{
    ButtonDefault
  },
  data() {
    return {
      hoverPinkButton: false,
      hoverPurpleButton: false,
      hoverOutPinkButton: false,
      hoverOutPurpleButton: false,
    };
  },
  methods: {
    controllerPinkButtonMouseleave() {
      this.hoverPinkButton = false;
      this.hoverOutPinkButton = true;
      this.hoverOutPurpleButton = false;
    },
    controllerPinkButtonMouseover() {
      this.hoverPinkButton = true;
      this.hoverOutPinkButton = false;
      this.hoverOutPurpleButton = false;
    },
    controllerPurpleButtonMouseleave() {
      this.hoverPurpleButton = false;
      this.hoverOutPurpleButton = true;
      this.hoverOutPinkButton = false;
    },
    controllerPurpleButtonMouseover() {
      this.hoverPurpleButton = true;
      this.hoverOutPurpleButton = false;
      this.hoverOutPinkButton = false;
    },
  },
};
</script>

<style scoped lang="scss">
section {
  height: 100%;
  background-color: #693668;
  margin: 0;
}
.polygon {
  background-color: #a74482;
  position: absolute;
  clip-path: polygon(0 0, 60% 0, 20% 100%, 0 100%);
  width: 100%;
  height: 100%;
  &GrowPink {
    animation: 0.5s polygon-increase;
    animation-fill-mode: forwards;
  }
  &RetractPink {
      animation: 0.5s polygon-increase-decrease;
      animation-fill-mode: forwards;
    }
  &GrowPurple {
    animation: 0.5s polygon-decrease;
    animation-fill-mode: forwards;

  }
  &RetractPurple {
      animation: 0.5s polygon-decrease-increase;
      animation-fill-mode: forwards;
    }
}
@keyframes polygon-increase {
  0% {
    clip-path: polygon(0 0, 60% 0, 20% 100%, 0 100%);
  }
  100% {
    clip-path: polygon(0 0, 70% 0, 30% 100%, 0 100%);
  }
}
@keyframes polygon-increase-decrease {
  0% {
    clip-path: polygon(0 0, 70% 0, 30% 100%, 0 100%);
  }
  100% {
    clip-path: polygon(0 0, 60% 0, 20% 100%, 0 100%);
  }
}
@keyframes polygon-decrease {
  0% {
    clip-path: polygon(0 0, 60% 0, 20% 100%, 0 100%);
  }
  100% {
    clip-path: polygon(0 0, 50% 0, 10% 100%, 0 100%);
  }
}
@keyframes polygon-decrease-increase {
  0% {
    clip-path: polygon(0 0, 50% 0, 10% 100%, 0 100%);
  }
  100% {
    clip-path: polygon(0 0, 60% 0, 20% 100%, 0 100%);
  }
}
.title {
  padding-top: 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;
  &-text {
    text-align: center;
    color: #f5f5f5;
    letter-spacing: 1px;
    font-size: 30px;
    margin-top: 0;
    &__highlight {
      background-image: linear-gradient(
        to bottom,
        transparent 55%,
        #1b1b3a 35%
      );
    }
  }
}
.buttons {
  margin-top: 100px;
  display: flex;
  justify-content: space-evenly;
  position: relative;
  flex-wrap: wrap;
}
@media screen and (max-width: 700px) {
  .buttons {
    gap: 20px;
  }
}
</style>

