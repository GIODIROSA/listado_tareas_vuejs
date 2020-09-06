<template>
  <div id="app">
    <div id="contenido">
      <!-- titulo del proyecto -->
      <h1 class="title">Listado de Tarea</h1>
      <!-- carga de las tareas -->
      <input
        v-model="tarea"
        type="text"
        @keyup.enter="agregarTareas"
        class="entrada"
      />
      <button @click="agregarTareas" class="btn-agregar">Agregar Tarea</button>
      <Tarea
        v-for="(tarea, i) in tareas"
        :key="i"
        :indice="i"
        :tarea="tarea"
        @vaciar="eliminarTarea"
        class="listado"
      />
    </div>
  </div>
</template>

<script>
import Tarea from "./components/Tarea";
export default {
  name: "App",
  data() {
    return {
      tarea: "",
      //recibe del input y del push
      tareas: [],
    };
  },
  components: {
    Tarea,
  },
  methods: {
    //carga de la tarea para el array
    agregarTareas() {
      if (this.tarea.trim()) {
        this.tareas.push(this.tarea);
        this.tarea = "";
      } else {
        alert("Debes ingresar una Tarea");
      }
    },
    //recibe de tarea componente el indice
    eliminarTarea(indice) {
      this.tareas.splice(indice, 1);
    },
  },
};
</script>

<style lang="scss" scoped>
//configuracion del listado
#app {
  display: flex;
  justify-content: center;
  align-content: center;
  background: #8d93ab;
}
.title {
  font-size: 50px;
  color: #393b44;
}
#contenido {
  width: 1000px;
  padding: 20px 150px;
  margin: 50px 0px;
  background: #d6e0f0;
  border-radius: 60px;
}
.listado {
  margin: 20px 0px;
}
.btn-agregar {
  padding: 10px;
  border: 0px;
  border-radius: 5px;
  margin: 20px;
  color: #d6e0f0;
  background-color: #393b44;
}
.entrada {
  padding: 10px;
  border-radius: 5px;
  border: 0px;
}
</style>
