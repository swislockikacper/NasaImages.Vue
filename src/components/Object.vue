<template>
  <div :style="objectImage"></div>
</template>

<script>
export default {
  name: "Object",
  props: {
    result: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      image: this.result.links[0].href,
      title: this.result.data[0].title
    };
  },
  computed: {
    objectImage() {
      return `background-image: url("${this.image}")`;
    }
  }
};
</script>

<style lang="scss" scoped>
div {
  width: 32vw;
  height: 22rem;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 50%;
}
</style>
