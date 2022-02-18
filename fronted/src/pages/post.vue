<template>
<div class="q-pa-md">
      <div>
          <q-card-section>
              <form v-on:submit.prevent="submitForm">
                <div class="no-margin full-height">
                    <label for="name">NOMBRE:</label>
                    <q-input square filled clearable required placeholder="INGRESAR NOMBRE" v-model="form.nombres"/>
                </div>
                 <div class="form-group">
                    <label for="email">CORREO</label>
                   <q-input square filled clearabletype="email" class="form-control" id="email" required placeholder="nombre@ejemplo.com"
                        v-model="form.correo"/>
                </div>
                 <div class="form-group">
                    <label for="name">DOCUMENTO:</label>
                   <q-input square filled clearabletype="number" class="form-control" id="name" required placeholder="INGRESAR DOCUMENTO" v-model="form.documento"/>
                </div>
                 <div class="form-group">
                    <label for="name">DE DONDE ES:</label>
                   <q-input square filled clearabletype="text" class="form-control" id="name" required placeholder="INGRESAR LUGAR DE NACIMIENTO" v-model="form.de_donde_es"/>
                </div>
                <div class="form-group">
                    <label for="name">DONDE TRABAJA:</label>
                   <q-input square filled clearabletype="text" class="form-control" id="name" required placeholder="INGRESAR LUGAR LABORAL" v-model="form.donde_trabaja"/>
                </div>
                <div class="form-group">
                    <label for="name">CARGO:</label>
                   <q-input square filled clearabletype="text" class="form-control" id="name" required placeholder="CARGO ACTUAL" v-model="form.cargo"/>
                </div>
                <div class="form-group">
                    <label for="name">SUELDO:</label>
                   <q-input square filled clearabletype="number" class="form-control" id="name" required placeholder="SUELDO" v-model="form.cuanto_gana"/>
                </div>
                <div class="form-group">
                    <label for="name">JEFE:</label>
                   <q-input square filled clearabletype="text" class="form-control" id="name" required placeholder="JEFE" v-model="form.jefe_inmediato"/>
                </div>
                 <div class="form-group">
                    <label for="name">TELEFONO:</label>
                   <q-input square filled clearabletype="text" class="form-control" id="name" required placeholder="TELEFONO" v-model="form.telefono"/>
                </div><br>
                <div class="form-group">
                     <q-btn unelevated color="light-blue-10" size="lg" q-btn value="Submit" type1="submit" type="submit"  class="full-width" label="AGREGAR" />
                </div>
            </form>
          </q-card-section>
      </div>
</div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'PostFormAxios',
  data () {
    return {
      form: {
        nombres: '',
        correo: '',
        documento: '',
        de_donde_es: '',
        donde_trabaja: '',
        cargo: '',
        cuanto_gana: '',
        jefe_inmediato: '',
        telefono: ''
      }
    }
  },
  methods: {
    submitForm () {
      console.log(this.form, 'hola')
      axios.post('http://localhost/api-php/api/create.php', this.form).then(res => {
        location.replace('/#/')
      })
    }
  }
}
</script>
