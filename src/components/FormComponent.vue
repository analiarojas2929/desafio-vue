<template>
  <div class="container">
    <h1>Desafío - Templates y Rendering en Vue</h1>
    
    <!-- Formulario para modificar la figura -->
    <div class="controls">
      <label>
        Color de fondo:
        <input type="color" v-model="backgroundColor" />
      </label>
      
      <label>
        Color de texto:
        <input type="color" v-model="textColor" />
      </label>

      <label>
        Mostrar texto:
        <input type="checkbox" v-model="showText" />
      </label>

      <label>
        Borde redondeado:
        <input type="range" min="0" max="50" v-model="borderRadius" />
      </label>

      <label>
        Contenido textual:
        <input type="text" v-model="textContent" placeholder="Escribe aquí..." />
      </label>

      <label>
        Tipografía:
        <select v-model="fontFamily">
          <option value="Arial">Arial</option>
          <option value="Courier New">Courier New</option>
          <option value="Cursive">Cursive</option>
        </select>
      </label>

      <label>
        Opaco:
        <input type="checkbox" v-model="isOpaque" />
      </label>

      <label>
        Tamaño de letra:
        <input type="radio" value="small" v-model="fontSize" /> Pequeño
        <input type="radio" value="medium" v-model="fontSize" /> Mediano
        <input type="radio" value="large" v-model="fontSize" /> Grande
      </label>
    </div>

    <!-- Figura modificable -->
    <div
      v-if="showShape"
      :style="figureStyle"
      class="figure"
    >
      <span v-if="showText">{{ textContent }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      backgroundColor: '#4caf50',
      textColor: '#ffffff',
      showText: true,
      textContent: 'Awesome Vue.js',
      fontFamily: 'Arial',
      fontSize: 'medium',
      isOpaque: true,
      borderRadius: 20,
      showShape: true,
    };
  },
  computed: {
    figureStyle() {
      return {
        backgroundColor: this.backgroundColor,
        color: this.textColor,
        borderRadius: this.borderRadius + '%',
        fontFamily: this.fontFamily,
        fontSize: this.getFontSize(),
        opacity: this.isOpaque ? 1 : 0.5,
        padding: '20px',
        display: 'flex',
        alignItems: 'center',
        justifyContent: 'center',
        width: '200px',
        height: '200px',
        margin: '20px auto',
      };
    },
  },
  methods: {
    getFontSize() {
      switch (this.fontSize) {
        case 'small':
          return '12px';
        case 'medium':
          return '16px';
        case 'large':
          return '24px';
        default:
          return '16px';
      }
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}
.controls {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 20px;
}
.figure {
  background-color: #4caf50;
  color: white;
  border: 2px solid #000;
}
</style>
