<template>
  <div>
    <form @submit.prevent>
      <input v-model="company.name" type="text" placeholder="наименование" class="input">
      <input v-model="company.address" type="text" placeholder="адрес" class="input">
      <input v-model="company.ogrn" type="text" placeholder="огрн" class="input">
      <input v-model="company.inn" type="text" placeholder="инн" class="input">
      <input v-model="company.date" type="text" placeholder="дата регистрации" class="input">
      <button @click="addCompany" class="btn btn-warning rounded-0">Добавить</button>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      company: {
        name: '',
        address: '',
        ogrn: '',
        inn: '',
        date: ''
      }
    }
  },
  methods: {
    addCompany() {
      this.company.id = Date.now();
      this.$emit('add', this.company);
      this.company = {
        name: '',
        address: '',
        ogrn: '',
        inn: '',
        date: ''
      }
      this.name = '';
      this.address = '';
      this.ogrn = '';
      this.inn = '';
      this.date = '';
    }
  }
}
</script>

<style>
  .btn {
    margin-top: 15px;
  }

  .input {
    width: 100%;
    padding: 10px 15px;
    margin-top: 15px;
  }
</style>