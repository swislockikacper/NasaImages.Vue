<template>
  <div class="container">
    <div class="image-container">
      <div class="image">
        <img :src="photo">
      </div>
    </div>
    <div class="about">
      <h1 class="title">{{ title }}</h1>
      <p class="description">{{ description }}</p>
    </div>
    <div class="close" @click="$emit('closeDetails')"/>
  </div>
</template>

<script>
export default {
  name: "Details",
  props: {
    result: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      photo: null,
      title: null,
      description: null
    };
  },
  mounted() {
    this.photo = this.result.links[0].href;
    this.title = this.result.data[0].title;
    this.description = this.result.data[0].description;
  }
};
</script>

<style scoped lang="scss" scoped>
.container {
  max-width: 100%;
  height: 100%;
  background: #666;
  position: relative;
  top: 0;
  right: 0;
  left: 0;

  .close {
    position: absolute;
    width: 2rem;
    height: 2rem;
    padding: 2rem;
    right: 0;
    top: 0;
    cursor: pointer;

    &::before,
    &::after {
      position: absolute;
      top: 2rem;
      right: 2rem;
      content: "";
      width: 2rem;
      height: 0.2rem;
      background: #000;
      display: block;
    }
    &::before {
      transform: rotate(45deg);
    }
    &::after {
      transform: rotate(-45deg);
    }
  }

  .image-container {
    display: flex;
    flex-direction: row;
    height: 100%;
    padding: 5rem;
    padding-bottom: 1rem;
    justify-content: center;
    align-items: center;

    .image {
      width: 100%;
      height: auto;
      background: #000;
      img {
        width: 100%;
        margin-bottom: 0;
      }
    }
  }

  .about {
    .title,
    .description {
      color: #fff;
      padding-top: 0;
      margin-top: 0;
      padding-left: 5rem;
      padding-right: 5rem;
    }

    .description {
      font-size: 1.4rem;
    }
  }
}
</style>
