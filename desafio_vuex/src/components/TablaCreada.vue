<script>
import { mapStores } from 'pinia'
import { useJuegosStore } from '@/stores/juegos'

export default {
  computed: {
    ...mapStores(useJuegosStore)
  },
  created() {
    this.juegosStore.fetchGames()
    console.log(this.juegosStore.juegos)
  },
  methods: {
    agregarStock(codigo) {
      this.juegosStore.agregarStock(codigo)
    },
    disminuirStock(codigo) {
      this.juegosStore.disminuirStock(codigo)
    }
  }
}
</script>

<template>
  <div>
    <h1 class="text-center">32 Bits</h1>
    <h2 class="text-center pb-4">Lista de juegos</h2>
    <table class="table border border-secondary-subtle text-center">
      <thead>
        <tr>
          <th>Codigo</th>
          <th>Nombre</th>
          <th>Stock</th>
          <th>Precio</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="juego in juegosStore.juegos" :key="juego.codigo">
          <td>{{ juego.codigo }}</td>
          <td>{{ juego.nombre }}</td>
          <td>{{ juego.stock }}</td>
          <td>{{ juego.precio }}</td>
          <td>
            <button @click="agregarStock(juego.codigo)" class="btn bg-green text-light mx-2">
              +
            </button>
            <button @click="disminuirStock(juego.codigo)" class="btn bg-red text-light">-</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style>
.bg-green {
  background-color: #10bb10;
  font-weight: 500;
}
.bg-green:hover {
  background-color: #10bb10;
  font-weight: 500;
  opacity: 0.7;
}
.bg-red {
  background-color: #f3111c;
  font-weight: 500;
}
.bg-red:hover {
  background-color: #f3111c;
  font-weight: 500;
  opacity: 0.7;
}
</style>
