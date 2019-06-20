<template>
  <tr class="table-people__row">
    <td class="table-people__id">{{person.id}}</td>
    <td class="table-people__first">{{person.firstName}}</td>
    <td class="table-people__last">{{person.lastName}}</td>
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
