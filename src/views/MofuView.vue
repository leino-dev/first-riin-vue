<script>
export default{
  data() {
    return {
      animal: ["うさぎ", "ハムスター", "チンチラ"],
      rabbit: {
        head: "丸くてかわいい",
        ears: "長くてかわいい",
        hand: "ふわふわでかわいい",
        belly: "ふかふか真っ白天使"
      },
      isShow: true
    }
  }
}
</script>

<template>
  <div class="about">
    <div v-if="isShow">
      <ul>
        <!-- arrayをforぐるぐる -->
        <li v-for="(item, index) in animal" :key="item">{{ index }}: {{ item }}</li>
      </ul>
      </div>

    <div>
      うさぎのかわいいところ
      <ul>
        <!-- objctをforぐるぐる -->
        <li v-for="(item, key) in rabbit" :key="item">{{ key }}: {{ item }}</li>
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
