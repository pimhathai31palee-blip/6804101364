<template>
  <q-page class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md" style="max-width: 600px">
      <q-input filled v-model="name" label="Your name (ชื่อ-สกุล) *" hint="Name and Surname" />
      <q-input filled type="number" v-model="age" label="Your age (อายุ) *" />
      <q-toggle v-model="accept" label="I accept the license and terms (我接受许可和条款语言)" />
      <div>
        <q-btn label="SUBMIT (提出する)" type="submit" color="primary" />
        <q-btn label="RESET (リセット)" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()
const name = ref(null)
const age = ref(null)
const accept = ref(false)

const onSubmit = () => {
  if (accept.value !== true) {
    $q.notify({
      color: 'red-5',
      textColor: 'white',
      icon: 'warning',
      message: 'You need to accept the license and terms first'
    })
  } else {
    $q.notify({
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
      message: 'Submitted'
    })
  }
}

const onReset = () => {
  name.value = null
  age.value = null
  accept.value = false
}
</script>