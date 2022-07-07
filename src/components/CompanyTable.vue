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
          <th scope="col">Изменить/Удалить</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="company in companies" :key="company.id">
          <td v-if="editing === company.id">
            <input type="text" v-model="company.name" />
          </td>
          <td v-else>{{company.name}}</td>
          <td v-if="editing === company.id">
            <input type="text" v-model="company.address" />
          </td>
          <td v-else>{{company.address}}</td>
          <td v-if="editing === company.id">
            <input type="text" v-model="company.ogrn" />
          </td>
          <td v-else>{{company.ogrn}}</td>
          <td v-if="editing === company.id">
            <input type="text" v-model="company.inn" />
          </td>
          <td v-else>{{company.inn}}</td>
          <td v-if="editing === company.id">
            <input type="text" v-model="company.date" />
          </td>
          <td v-else>{{company.date}}</td>
          <td v-if="editing === company.id">
            <button type="button" @click="editCompamy(company)">Сохранить</button>
          </td>
          <td v-else>
            <button type="button" @click="editMode(company.id)" class="btn btn-primary">
              <i class="fas fa-edit"></i>
            </button>
            <button type="button" @click="$emit('delete', company.id)" class="btn btn-danger">
              <i class="fas fa-trash-alt"></i>
            </button>
          </td>
        </tr>
      </tbody>
    </table>   
  </div>
</template>

<script>

export default {
  data() {
    return {
      editing: null
    };
  },
  props: {
    companies: {
      type: Array,
      required: true
    }
  },
  methods: {
    editMode(index) {
      this.editing = index;
    },
    editCompamy(company) {
      if (company.name === "" || company.address === "" || company.ogrn === "" || company.inn === "" || company.date === "")
        return;
      this.$emit("edit", company.id, company);
      this.editing = null;
    }
  }
}
</script>

<style>
table, th, td {
  text-align: center;
  border: none;
  font-size: 1.1em;
}
thead {
  background-color: #56ccb8;
}
</style>