<template>
  <div class="app">
    <h2 class="text-center mt-5">Список компаний</h2>
    <button @click="showWindow" class="btn btn-warning rounded-0">Добавить</button>
    <window-form v-model:show="windowVisible">
      <add-form 
        @add="addCompany"
      />
    </window-form>
    <company-table 
      :companies="companies"
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
          ogrn: '11',
          inn: '111',
          date: '01.01.2022'
        },
        {
          name: 'компания2',
          address: 'улица2',
          ogrn: '22',
          inn: '222',
          date: '02.02.2022'
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
    showWindow() {
      this.windowVisible = true;
    },
    inputName(event) {
      this.name = event.target.value;
    }
  }
}
</script>

<style>
  .app {
    padding: 20px;
  }
</style>
