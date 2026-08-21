<template>
  <q-page class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md" style="max-width: 600px">
      <q-input filled v-model="name" label="您的姓名 *" hint="姓氏和名字" />
      <q-input filled type="number" v-model="age" label="您的年龄 *" />
      <q-toggle v-model="accept" label="我接受许可和条款" />
      <div>
        <q-btn label="提交" type="submit" color="primary" />
        <q-btn label="重置" type="reset" color="primary" flat class="q-ml-sm" />
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
      message: '您需要先接受许可和条款'
    })
  } else {
    $q.notify({
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
      message: '提交成功'
    })
  }
}

const onReset = () => {
  name.value = null
  age.value = null
  accept.value = false
}
</script>