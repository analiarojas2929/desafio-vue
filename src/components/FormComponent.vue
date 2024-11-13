<template>
  <div class="container">
    <!-- Sección de controles (lado izquierdo) -->
    <div class="controls">
      <label>
        <span>Color de fondo:</span>
        <input type="color" v-model="backgroundColor" />
      </label>

      <label>
        <span>Color de texto:</span>
        <input type="color" v-model="textColor" />
      </label>

      <label>
        <span>Mostrar texto:</span>
        <input type="checkbox" v-model="showText" />
      </label>

      <label>
        <span>Borde redondeado:</span>
        <input type="range" min="0" max="50" v-model="borderRadius" />
      </label>

      <label>
        <span>Contenido textual:</span>
        <textarea v-model="textContent" rows="2" placeholder="Escribe aquí..."></textarea>
      </label>

      <label>
        <span>Tipografía:</span>
        <select v-model="fontFamily">
          <option value="Arial">Arial</option>
          <option value="Courier New">Courier New</option>
          <option value="Cursive">Cursive</option>
        </select>
      </label>

      <label>
        <span>Opaco:</span>
        <input type="checkbox" v-model="isOpaque" />
      </label>

      <div class="font-size">
        <span>Tamaño de letra:</span>
        <label>
          <input type="radio" value="small" v-model="fontSize" /> Pequeño
        </label>
        <label>
          <input type="radio" value="medium" v-model="fontSize" /> Mediano
        </label>
        <label>
          <input type="radio" value="large" v-model="fontSize" /> Grande
        </label>
      </div>
    </div>

    <!-- Figura modificable (lado derecho) -->
    <div v-if="showShape" :style="figureStyle" class="figure">
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
        transition: 'all 0.3s ease-in-out',
        boxShadow: '0 4px 8px rgba(0, 0, 0, 0.1)',
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
/* Contenedor principal */
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 90px;
  max-width: 800px;
  margin: 40px auto;
  padding: 20px;
}

/* Sección de controles (lado izquierdo) */
.controls {
  flex: 1;
  width: 350px;
  background-color: #2c3e50;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  color: #ecf0f1;
}

.controls label {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 15px;
}

.controls label span {
  flex: 1;
}

textarea {
  resize: none;
  width: 100%;
  padding: 5px;
  border-radius: 5px;
}

input[type="color"],
textarea,
select {
  flex: 2;
  padding: 5px;
  border: none;
  border-radius: 5px;
  background-color: #ecf0f1;
  color: #2c3e50;
}

input[type="checkbox"],
input[type="radio"] {
  margin-left: 10px;
}

input[type="range"] {
  width: 100%;
}

.font-size {
  display: flex;
  align-items: center;
  gap: 10px;
}

/* Figura (lado derecho) */
.figure {
  flex: 1;
  display: flex;
  align-items: center;
  background-color: #27ae60;
  color: white;
  border: 2px solid #fff;
  text-align: center;
  transition: all 0.3s ease;

}
</style>
