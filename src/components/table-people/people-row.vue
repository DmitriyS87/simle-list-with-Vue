<template>
  <tr class="table-people__row">
    <td class="table-people__cell">{{person.id}}</td>
    <td class="table-people__cell">{{person.firstName}}</td>
    <td class="table-people__cell">{{person.lastName}}</td>
  </tr>
</template>
<script>
export default {
  props: {
    person: {
      type: Object,
      required: true
    }
  }
};
</script>
<style>
</style>
