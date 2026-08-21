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
<<<<<<< HEAD
<<<<<<< HEAD
      message: 'คุณต้องยอมรับเงื่อนไขและข้อตกลงก่อน'
=======
      message: '您需要先接受许可和条款'
>>>>>>> Chinese-language
=======
      message: '最初に規約に同意する必要があります'
>>>>>>> Japanese-language
    })
  } else {
    $q.notify({
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
<<<<<<< HEAD
<<<<<<< HEAD
      message: 'ยื่นแบบฟอร์มสำเร็จ'
=======
      message: '提交成功'
>>>>>>> Chinese-language
=======
      message: '送信されました'
>>>>>>> Japanese-language
    })
  }
}

const onReset = () => {
  name.value = null
  age.value = null
  accept.value = false
}
</script>