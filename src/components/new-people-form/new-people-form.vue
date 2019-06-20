<template>
  <section class="container">
    <form class="make-person" v-on:submit.prevent="$emit('addPerson', person)">
      <label for="first-name">
        First Name:
        <input
          v-on:change="HandlerChangeTextInput"
          type="text"
          name="firstName"
          id="first-name"
        >
      </label>

      <label for="last-name">
        Last Name:
        <input
          v-on:change="HandlerChangeTextInput"
          type="text"
          name="lastName"
          id="last-name"
        >
      </label>
      <button type="submit">Add person</button>
    </form>
  </section>
</template>
<script>
export default {
  data() {
    return {
      person: {
        firstName: "",
        lastName: ""
      }
    };
  },
  methods: {
    HandlerChangeTextInput(evt) {
      this.person[evt.target.name] = evt.target.value;
    }
  }
};
</script>
<style>
.make-person {
  width: 300px;
}
</style>
