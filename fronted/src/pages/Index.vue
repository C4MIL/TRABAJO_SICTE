<template>
<div class="q-pa-md">
    <q-markup-table>
        <thead>
            <tr>
            <th>NOMBRE</th>
            <th>ID</th>
            <th>LUGAR_NAC</th>
            <th>TRABAJA EN</th>
            <th>CARGO</th>
            <th>SUELDO</th>
            <th>JEFE</th>
            <th>TEL</th>
            <th>EMAIL</th>
            <th>ULT_INGRESO</th>
            </tr>
        </thead>
        <tbody>
 <tr v-for="usuario in posts" :key="usuario.id">
            <td>{{ usuario.nombres }}</td>
            <td>{{ usuario.documento }}</td>
            <td>{{ usuario.de_donde_es }}</td>
            <td>{{ usuario.donde_trabaja }}</td>
            <td>{{ usuario.cargo }}</td>
            <td>{{ usuario.cuanto_gana }}</td>
            <td>{{ usuario.jefe_inmediato }}</td>
            <td>{{ usuario.telefono }}</td>
            <td>{{ usuario.correo }}</td>
            <td>{{ usuario.created }}</td>
          </tr>
        </tbody>
    </q-markup-table>
    <q-dialog v-model="editModal" @hide="cancelEditEmployee">
        <q-card style="width: 700px; max-width: 80vw;" v-if="employee !== null">
            <q-card-section>
                <div class="text-h6">Employee: {{employee.name}}</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
                <q-input outlined v-model="employee.name" label="Name" class="q-mb-md" />

                <q-input outlined v-model="employee.employee_salary" label="Salary" class="q-mb-md" type="number" />

                <q-input outlined v-model="employee.employee_age" label="Age" class="q-mb-md" type="number" />
            </q-card-section>

            <q-card-actions align="center" class="bg-white text-teal">
                <q-btn label="Save" color="positive" @click="saveEmployee" v-close-popup />
                <q-btn color="negative" label="Cancel" v-close-popup />
            </q-card-actions>
        </q-card>
    </q-dialog>
</div>
</template>

<script>
import { defineComponent } from 'vue'
import axios from 'axios'
export default defineComponent({
  name: 'PageIndex',
  data () {
    return {
      posts: [],
      errors: []
    }
  },
  created () {
    axios
      .get('http://localhost/api-php/api/read.php')
      .then(response => {
        this.posts = response.data
        console.log(response.data.nombres)
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
})
</script>
