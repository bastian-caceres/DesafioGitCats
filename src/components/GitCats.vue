<template>

    <!-- card -->
    <div class="card mx-auto my-5 text-center border-dark" style="width: 30rem;">
      <div class="card-body">
        <h5 class="card-title">Opten tu GifCats</h5>
        <form class="text-dark" @submit.prevent="mostrarGato">
          <!-- titulo -->  
          <div class="col-auto">
            <div class="input-group mb-2">
              <div class="input-group-prepend">
                <div class="input-group-text">Titulo</div>
              </div>
              <input type="text" class="form-control" placeholder="Ej: gatitos" v-model="titulo" required>
            </div>
          </div>

          <!-- filtro -->
          <div class="input-group mb-2 col-auto">
            <div class="input-group-prepend">
              <label class="input-group-text">Filtro</label>
            </div>
            <select class="form-control" v-model="filtro" required>
              <option value="blur">Blur</option>
              <option value="mono">Mono</option>
              <option value="sepia">Sepia</option>
              <option value="negative">Negative</option>
              <option value="paint">Paint</option>
              <option value="pixel">Pixel</option>
            </select>
          </div>

          <!-- color -->
          <div class="input-group mb-2 col-auto">
            <div class="input-group-prepend">
              <label class="input-group-text">Color</label>
            </div>
            <select class="form-control" v-model="color.background" required>
              <option value="red">Red</option>
              <option value="blue">Blue</option>
              <option value="yellow">Yellow</option>
              <option value="green">Green</option>
              <option value="orange">Orange</option>
            </select>
          </div>
          <!-- circulo -->
          <div class="circulo text-center rounded-circle m-auto" :style="color"></div>

          <!-- tamaño -->
          <div class="col-auto mt-2">
            <div class="input-group mb-2">
              <div class="input-group-prepend">
                <div class="input-group-text">Tamaño Letra</div>
              </div>
              <input type="text" class="form-control" placeholder="Ej: 20 = 20px" v-model="tamano" required>
            </div>
          </div>

          <!-- boton que genera todo -->
          <button type="submit">Generar GifCat</button>

        </form> 
        
      </div>
      <!-- imagen generada -->
      <img :src="link" alt="">
    </div>

</template>

<script>
export default {
  name: 'GitCats',
  props:{
    gifgato:{
      typr: Array,
      required: true
    }
  },
  data() {
    return {
      titulo: "",
      filtro: "",
      tamano: "",
      link: "",
      color:{
        background: ""
      }
    }
  },
  methods: {
    mostrarGato(){
      let titulo = this.titulo;
      let filtro = this.filtro;
      let color = this.color;
      let tamano = this.tamano;
      this.link = `https://cataas.com/cat/gif/says/${titulo}?filter=${filtro}&color=${color.background}&size=${tamano}`;
    }      
  },
}
</script>

<style scoped>
  .circulo{
    border: 1px solid black;
    width: 25px;
    height: 25px;
  }
  
  .red {
    background-color: red;
  }

  .blue {
    background-color: blue;
  }

  .yellow {
    background-color: yellow;
  }

  .green {
    background-color: green;
  }

  .orange {
    background-color: orange;
  }
</style>
