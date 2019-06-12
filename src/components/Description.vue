<template>
  <div>
    <h1>ASTRO</h1>
    <p>Type object which you want to search in cosmos.</p>
    <div class="logo"></div>
  </div>
</template>

<script>
export default {
  name: "Description"
};
</script>

<style scoped lang="scss" scoped>
div {
  display: flex;
  flex-direction: column;
  color: #fff;

  h1 {
    margin-left: auto;
    margin-right: auto;
    font-size: 8rem;
    margin-bottom: 0;
  }

  p {
    margin-left: auto;
    margin-right: auto;
    font-size: 2rem;
  }

  .logo {
    background-image: url(../assets/1.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
    width: 100%;
    height: 100vh;
  }
}
</style>
