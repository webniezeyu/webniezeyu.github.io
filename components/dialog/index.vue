<template>
  <Overlay
    :lockScroll="lockScroll"
    :opacity="opacity"
    :zIndex="zIndex"
    :isShow="isShow"
    :slotPosition="slotPosition"
  >
    <div class="n-dialog__init" :style="dialogStyle" :class="name">
      <div class="n-dialog__title">
        <slot name="title">
          <div>{{ title }}</div>
        </slot>
      </div>

      <div class="n-dialog__content">
        <slot name="content">
          <div>{{ content }}</div>
        </slot>
      </div>

      <div class="n-dialog__footer" v-if="isShowButton === true">
        <slot name="footer">
          <div class="btns" @click="cancel">取消</div>
          <div class="btns" @click="confirm">确认</div>
        </slot>
      </div>
    </div>
  </Overlay>
</template>
<script>
import { toRefs, reactive, isProxy, nextTick } from "vue";
import Overlay from "../overlay/index.vue";

export default {
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
      default: "center",
    },

    dialogStyle: {
      type: Object,
      default: {
        height: "200px",
      },
    },
    title: {
      type: String,
      default: "标题",
    },
    content: {
      type: String,
      default: "这是一个非常好用的基于Vue3的H5移动端组件Dialog",
    },
    isShowButton: {
      type: Boolean,
      default: true,
    },
    cancelCallback: {
      type: Function,
      default: () => {},
    },
    confirmCallback: {
      type: Function,
      default: () => {},
    },
  },
  components: {
    Overlay,
  },
  setup(props) {
    const className = reactive({
      name: ["n-popup__init", "border"],
    });

    return {
      ...toRefs(className),
      ...toRefs(props),
      cancel: () => {
        props.cancelCallback();
      },
      confirm: () => {
        props.confirmCallback();
      },
    };
  },
};
</script>
<style scoped>
.n-popup__init {
  width: 100vw;
  background-color: #ffffff;
}
.border {
  border-radius: 10px;
}
.borderBottom {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}

.borderTop {
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

.n-dialog__init {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.n-dialog__title {
  height: 40px;
  text-align: center;
  font-size: 20px;
  width: 100%;
  line-height: 40px;
  border-bottom: 1px solid #cccccc;
}
.n-dialog__content {
  height: auto;
  padding: 10px 20px;
  flex: 1;
}

.n-dialog__footer {
  border-top: 1px solid #cccccc;
  display: flex;
  height: 40px;
  justify-content: space-between;
}
.btns {
  letter-spacing: 1em;
  width: 50%;
  height: 100%;
  text-align: center;
  line-height: 40px;
}
.btns:first-child {
  border-right: 1px solid #cccccc;
}
</style>
