<script>
import { mapStores } from 'pinia'
import { useJuegosStore } from '@/stores/juegos'

export default {
  computed: {
    /**
     * useJuegosStore
     * juegosStore
     */
    ...mapStores(useJuegosStore)
  },
  created() {
    this.juegosStore.fetchGames()

    console.log(this.juegosStore.juegos)
  },
  methods: {
    agregarStock(idx) {
      this.juegosStore.agregarStock(idx)
    },
    disminuirStock(idx) {
      this.juegosStore.disminuirStock(idx)
    }
  }
}
</script>

<template>
  <div>
    <h1>Tabla</h1>

    <table class="table table-info table-striped">
      <thead>
        <tr>
          <th>Código</th>
          <th>Nombre</th>
          <th>Stock</th>
          <th>Precio</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(juego, idx) in juegosStore.juegos" :key="juego.codigo">
          <td>{{ juego.codigo }}</td>
          <td>{{ juego.nombre }}</td>
          <td>{{ juego.stock }}</td>
          <td>{{ juego.precio }}</td>
          <td>
            <button @click="agregarStock(idx)">Agregar</button>
            <button @click="disminuirStock(idx)">Dismuir</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style></style>
