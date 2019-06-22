<template>
  <section class="wrapper">
    <form class="make-person" v-on:submit.prevent="handleSubmit">
      <h4>Add new person:</h4>
      <label for="first-name" class="make-person__unit">
        First Name:
        <input
          v-on:change="HandlerChangeTextInput"
          type="text"
          name="firstName"
          class="make-person__input"
          id="first-name"
          placeholder="type text here"
        >
      </label>

      <label for="last-name" class="make-person__unit">
        Last Name:
        <input
          v-on:change="HandlerChangeTextInput"
          type="text"
          name="lastName"
          class="make-person__input"
          id="last-name"
          placeholder="type text here"
        >
      </label>
      <button type="submit" class="make-person__button">
        <span class="button__text">Add person</span>
      </button>
      <p v-if="errors.length">
        <b>Пожалуйста исправьте указанные ошибки:</b>
        <ul>
          <li v-for="error in errors" :key="error">{{ error }}</li>
       </ul>
      </p>
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
      },
      errors: []
    };
  },
  methods: {
    HandlerChangeTextInput(evt) {
      this.person[evt.target.name] = evt.target.value;
    },
    checkForm: function() {
      if (this.person.firstName && this.person.lastName) {
        return true;
      }

      this.errors = [];

      if (!this.person.firstName) {
        this.errors.push("Требуется указать имя.");
      }
      if (!this.person.lastName) {
        this.errors.push("Требуется указать фамилию.");
      }
    },
    handleSubmit() {
      if (this.checkForm()) {
        this.errors = [];
        this.$emit("add_person", this.person);
      }
    }
  }
};
</script>
<style>
.wrapper {
  padding: 20px 40px;
}
.make-person {
  width: 300px;
  border: 1px solid lightblue;
  border-radius: 5px;
  padding: 15px 15px 30px 25px;
  background-color: lightblue;
  color: orangered;
}
.make-person__button {
  margin: 10px 0 10px 0;
  padding: 10px 15px;
  border-radius: 5px;
  border-width: 0px;
  color: lightblue;
  background-color: orangered;
  font-size: 18px;
  box-shadow: 0px 0px 0px 1px rgba(255, 69, 0, 1);
}
.make-person__button:hover {
  box-shadow: 5px 5px 10px 0px rgba(255, 69, 0, 0.5);
}

.make-person__button:hover .button__text {
  color: black;
}
.make-person__unit {
  display: block;
  padding: 5px 0;
}
.make-person__unit:hover {
  color: black;
}

.make-person__input {
  border-width: 0px;
  border-radius: 1px;
  line-height: 24px;
  padding: 2px 5px;
}
</style>
