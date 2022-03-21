<template>
  <div class="container">
    <h1 class="text-center mb-3">Listado de Canciones</h1>
    <div class="row mt-5">
      <div class="col-4">
        <form @submit.prevent="submit">
          <div class="mb-3">
            <input class="form-control" type="text" v-model="artista"/>
            <input class="form-control" type="text" v-model="cancion"/>
          </div>
          <button class="btn btn-success">Buscar Canción</button>
        </form>
      </div>
      <div class="col-8">
        <p>Nombre Artista: {{artista}}</p>
        <p>Cancion: {{cancion}}</p>
        <p>letra de la cancion</p>
      </div>
    </div>
  </div>
</template>

<script>
import { consumirCanciones } from "./api";
export default {
  name: "App",
  components: {},
  data() {
    return {
      artista: "",
      cancion: "",
    };
  },
  methods: {
    async submit() {
      console.log('Se ejecuta el método submit')

      // 1 ejemplo
      //consumirCanciones(this.artista, this.cancion).then( letra => console.log(letra.lyrics));

      // 2 Ejemplo

      const letraCancion = await consumirCanciones(this.artista, this.cancion);
      console.log(letraCancion);
    }
  }

};
</script>

<style>
</style>
