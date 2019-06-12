<template>
  <input type="text" :value="value" @input="searchData" :class="{ dark: status === 1 }">
</template>

<script>
export default {
  name: "SearchInput",
  props: {
    value: {
      type: String,
      required: true
    },
    status: {
      type: Number,
      required: true
    }
  },
  methods: {
    searchData(event) {
      this.$emit("input", event.target.value);
    }
  }
};
</script>

<style lang="scss" scoped>
input {
  display: flex;
  margin-left: auto;
  margin-right: auto;
  width: 18rem;
  height: 2rem;
  border: 0;
  border-bottom: 0.15rem solid #fff;
  color: #fff;
  background: none;
  font-size: 1.8rem;
  text-align: center;

  &.dark {
    margin-top: 2.5rem;
    background: #444;
  }
}
</style>
