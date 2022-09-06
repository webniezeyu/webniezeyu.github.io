<template>
  <Overlay
    :lockScroll="lockScroll"
    :opacity="opacity"
    :zIndex="zIndex"
    :isShow="isShow"
    :slotPosition="slotPosition"
  >
    <div :style="popupStyle" class="n-popup__init">
      <slot></slot>
    </div>
  </Overlay>
</template>
<script>
import { toRefs, reactive, isProxy } from "vue";
import Overlay from "../overlay/index.vue";

export default {
  name: "n-popup",
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
      default: false,
    },
    lockScroll: {
      type: Boolean,
      default: true,
    },
    slotPosition: {
      type: String,
      default: "bottom",
    }, // Overlay-props
    popupHeight: {
      type: String,
      default: "200px",
    },
    popupStyle: {
      type: Object,
      default: {
        height: "200px",
      },
    },
    isRound: {
      type: Boolean,
      default: false,
    },
  },
  components: {
    Overlay,
  },
  setup(props) {
    if (props.isRound && props.slotPosition === "bottom") {
      props.popupStyle.borderTopLeftRadius = "10px";
      props.popupStyle.borderTopRightRadius = "10px";
    } else if (props.isRound && props.slotPosition === "top") {
      props.popupStyle.borderBottomLeftRadius = "10px";
      props.popupStyle.borderBottomRightRadius = "10px";
    } else if (props.isRound && props.slotPosition === "center") {
      props.popupStyle.borderRadius = "10px";
      props.popupStyle.borderRadius = "10px";
    }
    return {
      ...toRefs(props),
    };
  },
};
</script>
<style scoped>
.n-popup__init {
  width: 100vw;
  background-color: #ffffff;
}
</style>
