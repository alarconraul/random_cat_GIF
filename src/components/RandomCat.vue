<template>
  <div>
    <h1>{{ msg }}</h1>
    <form @submit.prevent="thisWillShowYouACat">
      <div class="form__input-container">

        <div class="row form-group">
          <div class="col-6 d-flex flex-column align-items-end">
            <label for="text">Título</label>
            <label for="text">Filtro</label>
            <label for="text">Color</label>
            <label for="text">Tamaño</label>
          </div>
          <div class="col-6 d-flex flex-column align-items-start">
            <input v-model="title" type="text">
            <select v-model="filter" name="" id="">
              <option disabled value="">Please, select a filter</option>
              <option>Blur</option>
              <option>Mono</option>
              <option>Sepia</option>
              <option>Negative</option>
              <option>Paint</option>
              <option>Pixel</option>
            </select>
            <div class="d-flex">
              <select v-model="color" name="" id="">
                <option disabled value="">Please, select a color</option>
                <option value="red">Rojo</option> 
                <option value="blue">Azul</option>
                <option value="green">Verde</option>
                <option value="white">Blanco</option>
                <option value="yellow">Amarillo</option>
              </select>
              <div class="circulo" :style="{'background-color':color}"></div>
            </div>
            <input v-model.number="size" type="number">
          </div>
        </div>
      </div>
      <input class="mt-3" type="submit" value="Obtener mi Gatito">
    </form>
    <img :src="image" alt="">
  </div>
</template>

<script>
export default {
  name: 'RandomCats',
  props: {
    msg: String,
  },
  data() {
    return {
      title: "",
      filter: "",
      color: "",
      size: 0,
      image: ""
    }
  },

  methods:{
    thisWillShowYouACat(){
      fetch(`https://cataas.com/cat/gif/says/${this.title}?filter=${this.filter}&color=${this.color}&size=${this.size}`)
        .then(data => this.image = data.url) 
        }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-size: 2em;
  font-weight: 700;
  text-align: center;
  padding: 2em 0 1em;
}
.form__input-container {
  background-color: lightcoral;
  padding: 2em;
}
.circulo {
  height: 50px;
  width: 50px;
  border-radius: 50%;
  display: inline-block;
  margin-left: 1em;
}
</style>