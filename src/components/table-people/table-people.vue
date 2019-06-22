<template>
  <section class="main">
    <h4>Our members:</h4>
    <table class="table-people">
      <tr class="table-people__row">
        <th @click="$emit('sortPersons', `id`)" class="table-people__cell table-people_head">
          #
          <SortArrow :name="`id`" :sortBy="sortBy" :asc="asc"/>
        </th>
        <th @click="$emit('sortPersons', `firstName`)" class="table-people__cell table-people_head">
          First name
          <SortArrow :name="`firstName`" :sortBy="sortBy" :asc="asc"/>
        </th>
        <th @click="$emit('sortPersons', `lastName`)" class="table-people__cell table-people_head">
          Last name
          <SortArrow :name="`lastName`" :sortBy="sortBy" :asc="asc"/>
        </th>
      </tr>
      <PeopleRow v-for="person in sortedPeople" :key="person.id" :person="person"/>
    </table>
  </section>
</template>
<script>
import PeopleRow from "../table-people/people-row";
import SortArrow from "../sort-arrow";
let personCounter = 1;
const arrowPath = function(asc) {
  return asc ? "./img/sort-direct-asc.svg" : "./img/sort-direct-desc.svg";
};
export default {
  components: {
    PeopleRow,
    SortArrow
  },
  props: {
    sortedPeople: Array,
    sortBy: String,
    asc: Boolean
  },
  methods: {
    handleClick() {}
  },
  computed: {
    sortConfig: function() {
      return {
        sortBy: this.sortBy,
        asc: this.asc
      };
    }
  }
};
</script>


<style>
.main {
  padding: 20px 40px;
  margin-bottom: 25px;
}

.table-people {
  display: table;
  border-collapse: collapse;
}

.table-people__row {
  border-bottom: 1px solid lightblue;
}

.table-people__cell {
  padding: 5px 15px;
}

.table-people_head {
  color: black;
  font-weight: bold;
  vertical-align: baseline;
}
</style>
