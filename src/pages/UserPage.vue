<template>
  <q-page padding class="user-background">
    <q-form>
      <div class="q-mb-md">
        <q-input v-model="name" label="Nome" outlined />
      </div>
      <div class="row q-col-gutter-x-md">
        <q-input class="col-8" mask="##/##/####" v-model="bornDate" label="Data de Nascimento" outlined>
          <template v-slot:append>
            <q-icon name="event" class="cursor-pointer">
              <q-popup-proxy>
                <q-date v-model="bornDate" mask="DD/MM/YYYY" />
              </q-popup-proxy>
            </q-icon>
          </template>
        </q-input>
        <q-select v-model="gender" class="col-4" label="Genero" outlined :options="[
          'Masculino',
          'Feminino',
          'Outro'
        ]" />
      </div>
      <div class="column">
        <q-checkbox v-model="term" label="Aceito os termos de uso" />
        <q-btn label="salvar" color="primary" @click="onSave" />
      </div>
    </q-form>
    <q-btn to='/' label=" voltar" />
  </q-page>
</template>

<script lang="ts">
import { useQuasar } from 'quasar'
import { defineComponent, ref } from 'vue'
export default defineComponent({
  name: 'UserPage',
  setup  () {
    const { notify } = useQuasar()

    const name = ref<string>('')
    const bornDate = ref<string>('')
    const gender = ref<string>('')
    const term = ref<boolean>(false)

    const onSave = () => {
      notify({
        message: `${name.value} salvo com sucesso`,
        type: 'positive'
      })
    }

    return {
      name,
      bornDate,
      gender,
      term,
      onSave
    }
  }
})
</script>

<style scoped>
.user-background {
    background-color: white;
}
</style>
