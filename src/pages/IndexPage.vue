<template>
  <q-page class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md" style="max-width: 600px">
      <q-input filled v-model="name" label="ชื่อของคุณ *" hint="ชื่อและนามสกุล" />
      <q-input filled type="number" v-model="age" label="อายุของคุณ *" />
      <q-toggle v-model="accept" label="ฉันยอมรับเงื่อนไขและข้อตกลง" />
      <div>
        <q-btn label="ยื่นแบบฟอร์ม" type="submit" color="primary" />
        <q-btn label="ล้างค่า" type="reset" color="primary" flat class="q-ml-sm" />
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
      message: 'คุณต้องยอมรับเงื่อนไขและข้อตกลงก่อน'
    })
  } else {
    $q.notify({
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
      message: 'ยื่นแบบฟอร์มสำเร็จ'
    })
  }
}

const onReset = () => {
  name.value = null
  age.value = null
  accept.value = false
}
</script>