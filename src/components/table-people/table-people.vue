<template>
  <section class="container">
    <table class="table-people">
      <tr class="table-people__row">
        <th @click="$emit('sortPersons', `id`)" class="table-people__id">#</th>
        <th @click="$emit('sortPersons', `firstName`)" class="table-people__first">First name</th>
        <th @click="$emit('sortPersons', `lastName`)" class="table-people__last">Last name</th>
      </tr>
      <PeopleRow v-for="person in sortedPeople" :key="person.id" :person="person"/>
    </table>
  </section>
</template>
<script>
import PeopleRow from "../table-people/people-row";

let personCounter = 1;

export default {
  components: {
    PeopleRow
  },
  props: {
    sortedPeople: Array
  }
};
</script>


<style>
#app {
  margin: 0 auto;
  line-height: 1.4;
  font-family: "Roboto", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #191919;
}
</style>
