<template>
  <div id="app">
    <TablePeople :sortedPeople="sortedPeople" v-on:sortPersons="setSortConfiguration"/>
    <NewPeopleForm v-on:addPerson="addPerson"/>
  </div>
</template>
<script>
import TablePeople from "./components/table-people/table-people.vue";
import NewPeopleForm from "./components/new-people-form/new-people-form.vue";

export default {
  components: {
    TablePeople,
    NewPeopleForm
  },
  data() {
    return {
      people: [
        {
          id: 0,
          firstName: "Петр",
          lastName: "Петров"
        },
        {
          id: 1,
          firstName: "Иван",
          lastName: "Иванов"
        },
        {
          id: 2,
          firstName: "Сергей",
          lastName: "Сергеев"
        }
      ],
      asc: true,
      sortBy: "id",
      page: 1,
      rowsPerPage: 10
    };
  },
  methods: {
    addPerson(newPerson) {
      const personCounter = this.people.length;
      this.people.push({
        id: personCounter,
        firstName: newPerson.firstName,
        lastName: newPerson.lastName
      });
    },
    setSortConfiguration(sortColumn) {
      if (sortColumn === this.sortBy) {
        return (this.asc = !this.asc);
      }
      this.asc = "asc";
      return (this.sortBy = sortColumn);
    }
  },
  computed: {
    sortedPeople: function() {
      return [...this.people].sort((a, b) => {
        if (a[this.sortBy] > b[this.sortBy]) {
          return this.asc ? 1 : -1;
        }
        if (a[this.sortBy] < b[this.sortBy]) {
          return this.asc ? -1 : 1;
        }
        return 0;
      });
    }
  }
};
</script>


<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
