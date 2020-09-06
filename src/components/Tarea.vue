<template>
  <div>
      <!-- pintar en pantalla la tarea y el btn que elimina la tarea -->
    {{ tarea }}
    <button @click="eliminar" class="delt">Eliminar Tarea</button>
  </div>
</template>

<script>
export default {
  name: "Tarea",
  props: {
    tarea: String,
    indice: Number,
  },
  methods: {
      //envia al padre el evento y el indice
    eliminar() {
      this.$emit("vaciar", this.indice);
    },
  },
};
</script>

<style lang="scss" scoped>
.delt {
  padding: 10px;
  color: #ea5455;
  border: 0px;
  border-radius: 60px;
  background-color: #40e0d0;
}
</style>
