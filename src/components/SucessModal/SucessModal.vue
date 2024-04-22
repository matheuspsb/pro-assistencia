<template>
  <div class="modal" v-show="showModal">
    <div class="modal-content">
      <img alt="confirmando dados" src="../../assets/check.png">
      <h2>Cadastro realizado com sucesso!</h2>
      <button @click="closeModal">Fazer novo cadastro</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showModal: false,
    };
  },
  methods: {
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 99;
}

.modal-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  width: 708px;
}

h2 {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 18px;
  font-weight: 700;
  line-height: 22px;
  text-align: center;
  color: #2e2e2e;
}

button {
  all: unset;
  width: 544px;
  max-height: 44px;
  border-radius: 8px;
  margin-top: 36px;
  padding: 12px 8px;
  background-color: #171559;
  cursor: pointer;

  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 700;
  line-height: 20px;
  color: #fefefe;
  text-align: center;
}
</style>
