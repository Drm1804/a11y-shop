<template>
  <div class="modal" @keyup.esc="click">
    <div class="mask" @click="click" ></div>
    <div class="window" role="dilog" aria-modal="true" aria-labelledby="dilog-title">
      <div class="text">
        <h3 id="dilog-title">
          Товар {{ title }} добавлен в колрзину, продолжить покупки или перейти
          в корзину?
        </h3>
        <div class="contrls">
          <button ref="first-button" @click="click">Продолжить покупки</button>
          <button @click="click">В корзину</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    title: String,
  },
  mounted() {
    this.$refs["first-button"].focus();
  },
  methods: {
    click() {
      this.$emit("close");
    },
  },
};
</script>


<style scoped>
.modal {
  text-align: left;
}
.window {
  position: fixed;
  width: 300px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  border-radius: 8px;
  padding: 8px 16px;
}

.mask {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: black;
  opacity: 0.6;
  z-index: 0;
}

.contrls {
  display: flex;
  justify-content: center;
  padding-bottom: 8px;
}
</style>
