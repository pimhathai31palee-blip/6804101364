<template>
  <q-page class="q-pa-md">
    <q-form class="q-gutter-md" style="max-width: 600px">
      <q-input filled label="Your name *" hint="Name and surname" />
      <q-input filled type="number" label="Your age *" />
      <q-toggle label="I accept the license and terms" />
      <div>
        <q-btn label="SUBMIT" type="submit" color="primary" />
        <q-btn label="RESET" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
  </q-page>
</template>