<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld 
      msg="Mensaje pasa al componente, " 
      titulo="Tarsicio Carrizales"
    />    
  </div>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-12">
        <h1>Personas</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <formulario-persona @add-persona="agregarPersona" />
        <tabla-personas 
          v-bind:personas="personas" 
          @delete-persona="eliminarPersona" 
          @actualizar-persona="actualizarPersona" 
        />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/hello/HelloWorld.vue'
import TablaPersonas from '@/components/persona/TablaPersonas.vue'
import FormularioPersona from '@/components/persona/FormularioPersona.vue'


export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    TablaPersonas,
    FormularioPersona
  },
  data() {
    return {
      personas: [
        {
          id: 1,
          nombre: 'Tarsicio',
          apellido: 'Carrizales',
          email: 'telecom.com.ve@gmail.com@gmail.com',
        },
        {
          id: 2,
          nombre: 'Carlos',
          apellido: 'Quevedo',
          email: 'carlosluis.quevedo@gmail.com',
        },
        {
          id: 3,
          nombre: 'Rommerc',
          apellido: 'Martinéz',
          email: 'rommercm@gmail.com',
        },
      ],
    }
  },
  methods: {
    agregarPersona(persona) {
      //let id = 0;
      
      if (this.personas.length > 0) {
        persona.id = this.personas[this.personas.length - 1].id + 1;
      }
      
      this.personas= [...this.personas, { ...persona}];
    },
    eliminarPersona(id) {
      this.personas = this.personas.filter(
        persona => persona.id !== id
      );
    },
    actualizarPersona(id, personaActualizada) {
      this.personas = this.personas.map(persona =>
        persona.id === id ? personaActualizada : persona
      )
    },
  }
}
</script>

<style>
  button {
    background: #009435;
    border: 1px solid #009435;
  }
</style>
