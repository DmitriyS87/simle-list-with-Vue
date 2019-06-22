<template>
  <div id="app">
    <div class="visually-hidden">
      <!-- Generator: Adobe Illustrator 23.0.3, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
      <svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
        <g id="sort_desc">
          <polygon stroke="#000000" stroke-miterlimit="10" points="8,2 1.1,14 14.9,14"></polygon>
        </g>
        <g id="sort_asc">
          <polygon stroke="#000000" stroke-miterlimit="10" points="8,14.5 14.9,2.5 1.1,2.5"></polygon>
        </g>
      </svg>
    </div>
    <div class="container">
      <h1>Table on Vue</h1>
    </div>
    <div class="container">
      <TablePeople
        :sortedPeople="sortedPeople"
        v-on:sortPersons="setSortConfiguration"
        :sortBy="sortBy"
        :asc="asc"
      />
      <NewPeopleForm v-on:add_person="addPerson"/>
    </div>
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
  flex-direction: column;
  justify-content: center;
  align-content: center;
  line-height: 1.4;
  font-family: "Roboto", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #191919;

  margin: 30px;
  border-radius: 15px;

  box-shadow: 0px 0px 5px 0px rgba(100, 100, 100, 0.05),
    0px 0px 5px 2px rgba(50, 50, 50, 0.1);
}
</style>
