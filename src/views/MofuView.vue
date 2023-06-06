<script>
export default{
  data() {
    return {
      animal: ["うさぎ", "ハムスター", "チンチラ"],
      isShow: true
    }
  }
}
</script>

<template>
  <div class="about">
    <div v-if="isShow">
      <ul>
        <li v-for="item in animal" :key="item">{{item}}</li>
      </ul>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
