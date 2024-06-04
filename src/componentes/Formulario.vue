<template>
  <section class="">
    <div class="d-flex flex-column align-items-center m-0">
      <div class="w-50 d-flex flex-column align-items-center">

        <h2 class="display-4 text-center m-2">Parcial PNT2</h2>

        <div
          class="mt-4 rounded border p-2"
          style="box-shadow: 3px 3px 2px lightgray; width: 60%"
        >
          <form novalidate @submit.prevent="">
            <div class="form-group">
              <label class="ml-1" for="texto">Texto:</label>
              <input
                id="texto"
                type="text"
                class="form-control"
                v-model.trim="texto"
              />
            </div>
          </form>
        </div>

        <div class="ml-2 mr-2 mt-4">
          <ol class="list-group">
            <li class="row">
              <p class="mr-2">1.</p>
              <span class="font-weight-light mr-2">Cantidad de caracteres del texto (trimmed): </span>
              <p>{{ cantCaracteres }}</p>
            </li>
            <li class="row">
              <p class="mr-2">2.</p>
              <span class="font-weight-light mr-2">Texto codificado: </span>
              <p>{{ codificado }}</p>
            </li>
            <li class="row">
              <p class="mr-2">3.</p>
              <span class="font-weight-light mr-2">Texto pasado a mayuscula: </span>
              <p>{{ aMayus }}</p>
            </li>
            <li class="row">
              <p class="mr-2">4.</p>
              <span class="font-weight-light mr-2">Texto pasado a minuscula: </span>
              <p>{{ aMinus }}</p>
            </li>
            <li class="row">
              <p class="mr-2">5.</p>
              <span class="font-weight-light mr-2">Texto intercalado empezando por mayuscula: </span>
              <p>{{ interPar }}</p>
            </li>
            <li class="row">
              <p class="mr-2">6.</p>
              <span class="font-weight-light mr-2">Texto intercalado empezando por minuscula: </span>
              <p>{{ interImpar }}</p>
            </li>
          </ol>
        </div>



        <hr>

        <span class="text-center mb-2">
          <h4>respuestas:</h4>
          <ol>
            <li>C</li>

            <li>C</li>
        
            <li>A</li>
          </ol>
        </span>

      </div>
    </div>
  </section>
</template>

<script>

function tablaFlip(letra){

  let isLower = (letra == letra.toLowerCase());
  let output = "";
  
  switch(letra.toLowerCase()) {
    case "a":
      output = "u"
      break;
    case "e":
      output = "o"
      break;
    case "o":
      output = "e"
    break;
    case "u":
      output = "a"
    break;
    default:
      output = letra;
  } 

  if(!isLower) { output = output.toUpperCase()}

  return output;

}

function codificador(texto){
  return Array.from(texto).map(letra => tablaFlip(letra)).join("");
}

function casePorParidad(texto, paridad = "par"){

  let par = (paridad == "par");

  return Array.from(texto).map( (letra, index) =>{ 
    // sumas la paridad que es un booleano entonces con solo eso podes mover el case
    return (index + par) % 2 ? letra.toUpperCase() : letra.toLowerCase();
  }).join("");

}

// funciones puras

export default {
  name: "src-componentes-parcial",
  components: {},
  props: [],
  data() {
    return {
      texto: "",
    };
  },
  computed: {
    cantCaracteres(){
      return this.texto.length;
    },
    codificado(){
      return codificador(this.texto);
    },
    aMayus(){
      return this.texto.toUpperCase();
    },
    aMinus(){
      return this.texto.toLowerCase();
    },
    interPar(){
      return casePorParidad(this.texto);
    },
    interImpar(){
      return casePorParidad(this.texto, "impar");
    }
  },
  methods: {

  },
};
</script>

<style>
label {
  text-transform: capitalize;
}
</style>
