<template>
    <VForm @submit.prevent="() => {}">
      <VRow>
        <VCol cols="12">
          <v-text-field
            v-model="formData.tc"
            label="TC"
            variant="outlined"
            :active="true"
          />
        </VCol>
        <VCol cols="12">
          <v-text-field
            label="Name"
            v-model="formData.name"
            variant="outlined"
            :active="true"
          ></v-text-field>
        </VCol>
  
        <VCol cols="12">
            <v-text-field
            label="Surname"
            v-model="formData.surname"
            variant="outlined"
            :active="true"
          ></v-text-field>
        </VCol>
        <VCol
          cols="12"
          class="text-end"
        >
          <v-btn type="submit" @click="fetchCreateEmployee(formData)"> Submit </v-btn>
        </VCol>
      </VRow>
    </VForm>
  </template>
  <script lang="ts" setup>
  import { ref } from "vue";
  import { useRouter } from 'vue-router'

  const router = useRouter()
const formData = ref({
    tc:"",
    name:"",
    surname:"",
})

const fetchCreateEmployee = async (formData) => {
 
    const response = await fetch(`/api/Employee`, {
      method: 'POST', 
      headers: {
        'Content-Type': 'application/json' 
      },
      body: JSON.stringify(formData)
    })
    const data = await response.json() 
    router.push('/employee')
}


  </script>
  