<script>
export default {
  data() {
    return {
      tamanoFuente: "40px",
      mostrarEstiloPersonalizado: false, // Estado del checkbox
      opaco: false,
      tipografia: "Arial",
      texto: "Hola!",
      tamanioBorde: 16,
      mostrarTexto: true,
      colorFondoSeleccionado: "black", // Color de fondo inicial
      colorTextoSeleccionado: "orange", // Color de texto inicial
      colores: [
        { nombre: "Rojo", valor: "red" },
        { nombre: "Verde", valor: "green" },
        { nombre: "Azul", valor: "blue" },
        { nombre: "Negro", valor: "black" },
        { nombre: "Blanco", valor: "white" },
        { nombre: "Amarillo", valor: "yellow" },
        { nombre: "Naranja", valor: "orange" },
        { nombre: "Morado", valor: "purple" }
      ]
    };
  }
};


</script>

<template>
  <div id="app">
    <div class="cuadro">
      <p>Color de fondo</p>
      <select v-model="colorFondoSeleccionado" id="coloresFondo">
        <option v-for="color in colores" :key="color.nombre" :value="color.valor">
          {{ color.nombre }}
        </option>
      </select>
      <p>Color de texto</p>
      <select v-model="colorTextoSeleccionado" id="coloresTexto">
        <option v-for="color in colores" :key="color.nombre" :value="color.valor">
          {{ color.nombre }}
        </option>
      </select>
      <p>mostrar texto</p>
      <label>
        <input type="checkbox" v-model="mostrarTexto" />
      </label>
      <p>Borde</p>
      <input type="range" v-model="tamanioBorde" min="12" max="36" id="tamanioBorde" />
      <p>Contenido textual</p>
      <input type="text" v-model="texto" id="inputTexto" />
      <p>Tipografía</p>
      <select v-model="tipografia" id="tipografia">
        <option value="Arial">Arial</option>
        <option value="Courier New">Courier New</option>
        <option value="Georgia">Georgia</option>
      </select>
      <p>Opaco</p>
      <input type="checkbox" v-model="opaco" />
      <p>Tamaño de letra</p>
      <div>
      <label style="color: white;">
        <input
          type="radio"
          value="20px"
          v-model="tamanoFuente"
        />
        Pequeño
      </label>
    </div>
    <div>
      <label style="color: white;">
        <input
          type="radio"
          value="40px"
          v-model="tamanoFuente"
        />
        Mediano
      </label>
    </div>
    <div>
      <label style="color: white;">
        <input
          type="radio"
          value="60px"
          v-model="tamanoFuente"
        />
        Grande
      </label>
    </div>

    </div>
    <div :style="{
      background: colorFondoSeleccionado,
      borderWidth: tamanioBorde + 'px',
      borderStyle: 'solid',
      borderColor: colorTextoSeleccionado,
      width: '400px',
      height: '434px',
      opacity: opaco ? 0.5 : 1,
    }">
      <h1 v-show="mostrarTexto" :style="{ 
        color: colorTextoSeleccionado,
        fontFamily: tipografia,
        fontSize: tamanoFuente,
        }"
        >{{ texto }}</h1>

    </div>
  </div>
</template>

<style scoped>
.cuadro {
  background-color: rgb(7, 84, 84);
}

p {
  color: white;
}
</style>
