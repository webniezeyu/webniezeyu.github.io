<template>
  <Transition name="nTransition">
    <div
      v-show="isShow"
      :class="className"
      :style="styleName"
      @touchmove="eventOnTouchMove"
    >
      <div :class="soltClassName" @click.stop="() => {}">
        <slot></slot>
      </div>
    </div>
  </Transition>
</template>
<script>
import { toRefs } from "vue";

export default {
  name: "n-overlay",
  props: {
    opacity: {
      type: Number,
      default: 0.5,
    },
    zIndex: {
      type: Number,
      default: 1,
    },
    isShow: {
      type: Boolean,
      default: true,
    },
    lockScroll: {
      type: Boolean,
      default: true,
    },
    slotPosition: {
      type: String,
      default: "bottom",
    },
  },
  setup(props) {
    const soltClassName = [
      "n-position__absolute",
      props.slotPosition === "top"
        ? "n-position__absolute__top"
        : "n-position__absolute__bottom",
    ];
    const className = ["n-overlay__init", "n-position__relative"];

    const styleName = {
      backgroundColor: `rgba(0, 0, 0, ${props.opacity})`,
      zIndex: props.zIndex,
    };

    const eventOnTouchMove = (e) => {
      if (props.lockScroll) {
        e.preventDefault();
      }
    };

    return {
      ...toRefs(props),
      className,
      styleName,
      eventOnTouchMove,
      soltClassName,
    };
  },
};
</script>
<style scoped>
.n-overlay__init {
  position: fixed;
  top: 0;
  width: 100vw;
  height: 100vh;
}
.nTransition-enter-active,
.nTransition-leave-active {
  transition: opacity 0.4s ease;
}
.nTransition-enter-from,
.nTransition-leave-to {
  opacity: 0;
}

.n-overlay__init {
  position: fixed;
  top: 0;
  width: 100vw;
  height: 100vh;
}
.nTransition-enter-from,
.nTransition-leave-to {
  opacity: 0;
}
.n-display__none {
  display: none;
}
.n-display__block {
  display: block;
}
.n-position__relative {
  position: fixed;
}

.n-position__absolute {
  position: fixed;
  left: 0;
}
.n-position__absolute__top {
  top: 0;
}

.n-position__absolute__bottom {
  bottom: 0;
}
</style>
