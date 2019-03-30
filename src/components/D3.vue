<template>
  <div class="test">Hello People!</div>
</template>

<script>
export default {
  data() {
    return {
      a: 1,
      b: 2
    };
  },
  computed: {
    c() {
      return this.a + this.b;
    }
  }
};
</script>
<style scoped >
.test {
  position: fixed;

  top: 400;
  height: 200px;
  width: 100px;
  background-color: yellow;
}
</style>
