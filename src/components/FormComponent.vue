<template>
    <div class="container">
      <h1>Desafío - Templates y Rendering en Vue</h1>
      <!-- Formulario para modificar estilos -->
      <div class="controls">
        <label>
          Color de fondo:
          <input type="color" v-model="backgroundColor" />
        </label>
        <label>
          Tamaño:
          <input type="range" min="50" max="300" v-model="size" />
        </label>
        <label>
          Mostrar figura:
          <input type="checkbox" v-model="isVisible" />
        </label>
        <button @click="toggleBorder">Alternar borde</button>
      </div>
  
      <!-- Figura a modificar -->
      <div 
        v-if="isVisible"
        :style="{ backgroundColor: backgroundColor, width: size + 'px', height: size + 'px' }"
        :class="{ bordered: hasBorder }"
        class="figure"
      >
        Figura
      </div>
  
      <!-- Lista generada dinámicamente -->
      <ul>
        <li v-for="(item, index) in items" :key="index">{{ item }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        backgroundColor: '#3498db',
        size: 150,
        isVisible: true,
        hasBorder: false,
        items: ['Elemento 1', 'Elemento 2', 'Elemento 3']
      };
    },
    methods: {
      toggleBorder() {
        this.hasBorder = !this.hasBorder;
      }
    }
  };
  </script>
  
  <style scoped>
  .container {
    text-align: center;
    margin-top: 50px;
  }
  .controls {
    margin-bottom: 20px;
  }
  .figure {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 20px auto;
    color: white;
  }
  .bordered {
    border: 5px solid black;
  }
  </style>
  