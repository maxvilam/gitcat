<template>
  <div id="app">
    <section>
      <h1 class="paddingcont">Random Git Cat</h1>
    </section>
    <section class="content">
      <p class="paddingcont">
        Titulo:
        <input type="text" v-model="titulo" />
      </p>
      <p>
        <label for="tipo">Filtro: </label>
        <select class="form-control" v-model="filtro">
          <option value="blur">blur</option>
          <option value="mono">mono</option>
          <option value="sepia">sepia</option>
          <option value="negative">negative</option>
          <option value="paint">paint</option>
          <option value="pixel">pixel</option>
        </select>
      </p>
      <section class="grupocolor">
        <label for="tipo">Color: </label>
        <select class="form-control" v-model="color">
          <option value="blue">Azul</option>
          <option value="yellow">Amarillo</option>
          <option value="green">Verde</option>
          <option value="white">Blanco</option>
          <option value="black">Negro</option>
        </select>
        <table :class="colorcircle" width="20" height="20"></table>
      </section>
      <p class="paddingcont">
        Tamaño: 
        <input v-model="tamanno" type="number" />
      </p>
    </section>
    <section class="footerimg">
      <p>
      <button @click="cambiaestado">Obtener mi gatito</button>
      </p>
      <img  :src="ruta" width="500px" height="auto" alt="" />
    </section>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      titulo: "Git-Kat",
      filtro: "blur",
      color: "green",
      tamanno: "40",
      saludoscat: "holi?filter=sepia&color=orange&size=40&type=or",
      URL: "https://cataas.com/cat/gif/says/",
      ruta: "",
      estado: true,
    };
  },
  methods: {
    cambiaestado() {
      
      return (this.ruta =  this.URL +
        this.titulo +
        "?filter=" +
        this.filtro +
        "&color=" +
        this.color +
        "&size=" +
        this.tamanno +
        "&type=or");
    },
  },
  computed: {
    mostrarocultar(){
      return {mostrar: this.estado, nomostrar: !this.estado}
    },
    colorcircle() {
      return {
        claseblue: this.color === "blue",
        claseyellow: this.color === "yellow",
        clasegreen: this.color === "green",
        clasewhite: this.color === "white",
        claseblack: this.color === "black",
      };
    },
/*     ruta() {
      return (
        this.URL +
        this.titulo +
        "?filter=" +
        this.filtro +
        "&color=" +
        this.color +
        "&size=" +
        this.tamanno +
        "&type=or"
      );
    },
 */  },
};
</script>

<style lang="scss">
.paddingcont{
  padding: 10px 0;
}
.footerimg {
  background-color: rgb(111, 215, 224);
}
.content {
  margin: 80px 0;
  background-color: rgb(233, 129, 129);
}
.title {

  background-color: rgb(111, 215, 224);
}
.grupocolor {
  display: flex;
  justify-content: center;
}
.claseblue {
  background-color: blue;
  border-radius: 50%;
}
.claseyellow {
  background-color: yellow;
  border-radius: 50%;
}
.clasegreen {
  background-color: green;
  border-radius: 50%;
}
.clasewhite {
  background-color: white;
  border-radius: 50%;
}
.claseblack {
  background-color: black;
  border-radius: 50%;
}
.margenes{
  margin-top: 0;
  margin-bottom: 0;
}
#app {
  background-color: rgb(111, 215, 224);
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
