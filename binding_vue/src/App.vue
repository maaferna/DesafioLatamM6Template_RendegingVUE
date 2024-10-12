<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-md-4 bg-dark text-light p-3">
        <form>
          <div class="form-group mb-3">
            <label for="bgColor">Color de fondo</label>
            <input type="text" v-model="bgColor" class="form-control" id="bgColor">
          </div>

          <div class="form-group mb-3">
            <label for="textColor">Color de texto</label>
            <input type="text" v-model="textColor" class="form-control" id="textColor">
          </div>

          <div class="form-group form-check mb-3">
            <input type="checkbox" v-model="showText" class="form-check-input" id="showText">
            <label class="form-check-label" for="showText">Mostrar texto</label>
          </div>

          <div class="form-group mb-3">
            <label for="borderSize">Borde</label>
            <input type="range" v-model="borderSize" min="0" max="20" class="form-range" id="borderSize">
          </div>

          <div class="form-group mb-3">
            <label for="fontStyle">Tipografía</label>
            <select v-model="fontStyle" class="form-control" id="fontStyle">
              <option value="sans-serif">Sans Serif</option>
              <option value="cursive">Cursive</option>
              <option value="monospace">Monospace</option>
              <option value="verdana">Verdana</option>
            </select>
          </div>

          <div class="form-group mb-3">
            <label for="textStyles">Estilos de texto</label>
            <select v-model="textDecoration" class="form-control" id="textStyles">
              <option value="normal">Normal</option>
              <option value="italic">Cursiva</option>
              <option value="underline">Subrayado</option>
              <option value="bold">Negrita</option>
              <option value="italic underline">Cursiva y Subrayado</option>
              <option value="italic bold">Cursiva y Negrita</option>
              <option value="bold underline">Negrita y Subrayado</option>
              <option value="italic underline bold">Cursiva, Subrayado y Negrita</option>
            </select>
          </div>

          <div class="form-check mb-3">
            <input type="checkbox" v-model="opaque" class="form-check-input" id="opaque">
            <label class="form-check-label" for="opaque">Opaco</label>
          </div>

          <div class="form-group mb-3">
            <label>Tamaño de letra</label>
            <div>
              <input type="radio" v-model="fontSize" value="small" id="sizeSmall">
              <label for="sizeSmall">Pequeño</label>

              <input type="radio" v-model="fontSize" value="medium" id="sizeMedium">
              <label for="sizeMedium">Mediano</label>

              <input type="radio" v-model="fontSize" value="large" id="sizeLarge">
              <label for="sizeLarge">Grande</label>
            </div>
          </div>
        </form>
      </div>

      <div class="col-md-8 d-flex justify-content-center align-items-center">
        <div
          class="rounded-circle d-flex justify-content-center align-items-center"
          :style="divStyles"
        >
          <span :class="textClass" v-show="showText">{{ content }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bgColor: 'green',
      textColor: 'white',
      showText: true,
      borderSize: 5,
      content: 'Awesome Vue.js',
      fontStyle: 'sans-serif',
      textDecoration: 'normal',
      opaque: true,
      fontSize: 'medium',
    };
  },
  computed: {
    divStyles() {
      return {
        backgroundColor: this.bgColor,
        color: this.textColor,
        borderWidth: this.borderSize + 'px',
        borderStyle: 'solid',
        borderRadius: '20%',
        fontSize: this.fontSizeMap[this.fontSize],
        fontFamily: this.fontStyle,
        opacity: this.opaque ? 1 : 0.5,
        padding: '20px',
        width: '200px',
        height: '200px',
        textAlign: 'center',
      };
    },
    textClass() {
      return {
        'font-weight-bold': this.textDecoration.includes('bold'),
        'text-italic': this.textDecoration.includes('italic'),
        'text-underline': this.textDecoration.includes('underline'),
      };
    },
    fontSizeMap() {
      return {
        small: '12px',
        medium: '18px',
        large: '24px',
      };
    }
  },
};
</script>

<style scoped>
.container-fluid {
  margin-top: 20px;
}
.text-italic {
  font-style: italic;
}
.text-underline {
  text-decoration: underline;
}
.font-weight-bold {
  font-weight: bold;
}
.form-group {
  margin-bottom: 20px;
}
</style>
