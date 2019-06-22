<template>
  <span v-if="sortBy === name" class="arrow__container">
    <svg v-if="asc" class="arrow">
      <use x="0" y="2" xlink:href="#sort_asc"></use>
    </svg>
    <svg v-else class="arrow">
      <use x="0" y="2" xlink:href="#sort_desc"></use>
    </svg>
  </span>
  <span v-else class="arrow__container">
    <div class="arrow"></div>
  </span>
</template>
<script>
export default {
  data() {
    return {
      src: {
        asc: "#sort_asc",
        desc: "#sort_desc"
      }
    };
  },
  props: {
    name: String,
    sortBy: String,
    asc: Boolean
  },
  computed: {
    getSrc: function() {
      return asc === true ? src.asc : src.desc;
    }
  }
};
</script>
<style>
.arrow__container {
  position: relative;
  display: inline;
  display: inline-block;
}
.arrow {
  position: relative;
  width: 16px;
  height: 16px;
}
</style>
