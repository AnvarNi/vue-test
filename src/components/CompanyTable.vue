<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Наименование</th>
          <th scope="col">Адрес</th>
          <th scope="col">ОГРН</th>
          <th scope="col">ИНН</th>
          <th scope="col">Дата регистрации</th>
          <th scope="col">Изменить</th>
          <th scope="col">Удалить</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(company, index) in companies" :key="index">
          <td>{{company.name}}</td>
          <td>{{company.address}}</td>
          <td>{{company.ogrn}}</td>
          <td>{{company.inn}}</td>
          <td>{{company.date}}</td>
          <td>
            <div @click="editCompany(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div @click="deleteCompany(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>   
  </div>
</template>

<script>
export default {
  props: {
    companies: {
      type: Array,
      required: true
    }
  },
  methods: {
    deleteCompany(index) {
      this.companies.splice(index, 1);
    },
    editCompany(index) {

    }
  }
}
</script>

<style>

</style>