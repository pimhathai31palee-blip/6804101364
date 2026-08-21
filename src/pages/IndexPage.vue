<template>
  <q-page class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md" style="max-width: 600px">
      <q-input filled v-model="name" label="お名前 *" hint="氏名" />
      <q-input filled type="number" v-model="age" label="年齢 *" />
      <q-toggle v-model="accept" label="規約に同意します" />
      <div>
        <q-btn label="送信" type="submit" color="primary" />
        <q-btn label="リセット" type="reset" color="primary" flat class="q-ml-sm" />
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
      message: '最初に規約に同意する必要があります'
    })
  } else {
    $q.notify({
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
      message: '送信されました'
    })
  }
}

const onReset = () => {
  name.value = null
  age.value = null
  accept.value = false
}
</script>