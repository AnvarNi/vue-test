<template>
  <div class="app">
    <h1 class="text-center mt-5">Список компаний</h1>
    <button @click="showWindow" class="btn btn-primary rounded">Добавить</button>
    <window-form v-model:show="windowVisible">
      <add-form 
        @add="addCompany"
      />
    </window-form>
    <company-table 
      :companies="companies"
      @delete="deleteCompany"
      @edit="editCompamy"
    />
  </div>
</template>

<script>
import AddForm from "@/components/AddForm";
import CompanyTable from "@/components/CompanyTable";
import WindowForm from "@/components/WindowForm";

export default {
  components: {
    AddForm, CompanyTable, WindowForm
  },

  data() {
    return {
      companies: [
        {
          name: 'компания1',
          address: 'улица1',
          ogrn: '1',
          inn: '11',
          date: '01.01.2022'
        }
      ],
      windowVisible: false,
    }
  },
  methods: {
    addCompany(company) {
      this.companies.push(company);
      this.windowVisible = false;
    },
    deleteCompany(id) {
      this.companies = this.companies.filter(company => company.id !== id)
    },
    editCompany(id, updateCompany) {
      this.companies = this.companies.map(company => company.id === id ? updateCompany : company);
    },
    showWindow() {
      this.windowVisible = true;
    },
    inputName(event) {
      this.name = event.target.value;
    },
  }
}
</script>

<style>
.app {
  padding: 20px;
}
.btn {
  margin-bottom: 20px;
}
</style>
