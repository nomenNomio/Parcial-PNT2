<template>
  <Navbar />
  <Formulario/>
  <Footer></Footer>
</template>

<script>

import Navbar from "./componentes/Navbar.vue";
import Footer from "./componentes/Footer.vue";
import Formulario from "./componentes/Formulario.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Footer,
    Formulario,
  },
};
</script>

<style></style>
