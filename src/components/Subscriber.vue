<template>
  <v-container class="">
    <v-responsive class="">
      <v-sheet width="300" class="mx-auto">
        <form @submit.prevent="submit">
          <v-text-field
            v-model="name.value.value"
            :error-messages="name.errorMessage.value"
            label="Name"
          ></v-text-field>

          <v-text-field
            v-model="lastname.value.value"
            :error-messages="lastname.errorMessage.value"
            label="Lastname"
          ></v-text-field>

          <v-text-field
            v-model="email.value.value"
            :error-messages="email.errorMessage.value"
            label="E-mail"
          ></v-text-field>

          <v-btn class="me-4" color="success" type="submit"> submit </v-btn>
        </form>
      </v-sheet>
    </v-responsive>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'
import { useField, useForm } from 'vee-validate'
import axios from "axios"
const { handleSubmit, handleReset } = useForm({
  validationSchema: {
    name (value) {
      if (value?.length >= 2) return true

      return 'Name needs to be at least 2 characters.'
    },
    lastname (value) {
      if (value?.length >= 2) return true

      return 'Name needs to be at least 2 characters.'
    },
    email (value) {
      if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true

      return 'Must be a valid e-mail.'
    },

  },
})
const name = useField('name')
const lastname = useField('lastname')
const email = useField('email')
const submit = handleSubmit(formData => {
  createuser(formData)
  handleReset();
    })

function createuser(formData) {

   axios.post('/api', {
  name: formData.name,
  lastname: formData.lastname,
  email: formData.email,
})
.then(function (response) {
 console.log(response)
 alert(response.data)

})
.catch(function (error) {
  console.log(error)
  alert(response.data)
  
});

}
</script>
