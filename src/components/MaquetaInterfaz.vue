<template>
  <main class="container">
    <form class="form">
      <fieldset>
        <label class="espacio">Escribe un color de fondo en español</label>
        <br />
        <input class="form-control ancho" v-model="colorCuadrado" />
        <br>
        <br>
        <label class="espacio">Escribe un color de letra en español</label>
        <br>
        
        <input class="form-control ancho" v-model="colorLetra" />
        <br>
        <br>
        <label class="espacio">Mostrar texto</label>
        <input v-model="show" type="checkbox" />
        <br>
        <br>
        <label for="customRange2" class="form-label ancho espacio">Borde</label>
        <br />
        <input
          v-model="border"
          type="range"
          class="form-range ancho"
          :min="minimo"
          :max="maximo"
          step="0.5"
          id="customRange2"
        />
        <br>
        <br>
        <label class="espacio">Contenido textual: </label>
        <br />
        <textarea maxlength="200" v-model="texto"></textarea>
        <br>
        <br>
        <label class="espacio">Tipografía: </label>
        <br />
        <select v-model="typography">
          <option
            :key="tipografia"
            v-for="tipografia in tipografias"
            :value="tipografia"
          >
            {{ tipografia }}
          </option>
        </select>
        <br>
        <br>
        <label class="espacio">Opaco</label>
        <input v-model="opaco" type="checkbox" />
      </fieldset>
      <fieldset>
        <label class="espacio">Tamaño de letra</label>
        <br>
        <br> 
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="p"
            value="1rem"
            v-model="size"
          />
          <label class="form-check-label" for="p"> Pequeño </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="m"
            value="1.5rem"
            v-model="size"
          />
          <label class="form-check-label" for="m"> Mediano </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="g"
            value="2rem"
            v-model="size"
          />
          <label class="form-check-label" for="g"> Grande </label>
        </div>
      </fieldset>
    </form>
    <figure
      id="cuadrado"
      :style="{
        background: colorFondoFormulario,
        color: colorTextoFormulario,
        borderRadius: radioCompleto,
        fontFamily: typography,
        fontSize: size,
      }"
      :class="{ opaco: opaco }"
    >
      <p v-if="show">{{ texto }}</p>
    </figure>
  </main>
</template>

<script>
export default {
  name: "ModificarCuadro",
  data() {
    return {
      colorCuadrado: "",
      colorLetra: "",
      show: "",
      border: "",
      minimo: "1",
      maximo: "50",
      texto: "",
      typography: "",
      opaco: false,
      size: "",
      tipografias: [
        "Times New Roman",
        "Georgia",
        "Arial",
        "Verdana",
        "Tahoma",
        "Sanvito",
        "Courier",
      ],
      colores: {
        "rojo": "#ff0000",
        "verde": "#008000",
        "azul": "#0000ff",
        "amarillo": "#ffff00",
        "naranja": "#ffa500",
        "rosa": "#ff69b4",
        "violeta": "#8a2be2",
        "morado": "#800080",
        "blanco": "#ffffff",
        "negro": "#000000",
        "gris": "#808080",
        "marrón": "#a52a2a",
        "celeste": "#87ceeb",
        "turquesa": "#40e0d0",
        "beige": "#f5f5dc",
        "cafe": "#964b00",
        "rosado": "#ffc0cb",
        "verde claro": "#90ee90",
        "amarillo claro": "#ffffe0",
        "azul claro": "#add8e6",
      },
    };
  },
  computed: {
    radioCompleto() {
      return this.border + "%";
    },
    colorFondoFormulario() {
      return this.colores[this.colorCuadrado.toLowerCase()] || "";
    },
    colorTextoFormulario() {
      return this.colores[this.colorLetra.toLowerCase()] || "";
    },
  },
};
</script>

<style>

.container {
  display: flex;
  align-items: stretch;
}

.form {
  background: #066168; 
  color: #000000; 
  display: inline-block;
  flex-direction: flex-start;
  text-align: left;
  padding: 40px;
  font-size: 16px;
  margin-top: 5rem;
}

.ancho, textarea, select {
  width: 250px;
}

#cuadrado {
  width: 400px;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #719c72;;
  margin-left: 50px;
  overflow: auto;
  padding: 1rem;
  align-self: center;
}

.opaco {
  opacity: 0.5; 
}
</style>
