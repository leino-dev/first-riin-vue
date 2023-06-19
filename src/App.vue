<script>
// import HelloWorld from './components/HelloWorld.vue';

export default{
  components: {
    // HelloWorld
  },
  data() {
    return {
      title: "もふもふこそ正義の国",
      isShow: true,
      count: 0,
      hoge: "mofumofu",
      isDisabled: true,
      pages: {
        "/": "Home",
        "/about": "About",
        "/mofu": "もふもふ",
        "/line": "リスト"
      },
      visible: false
    }
  },
  methods: {
    increment() {
      // ここで変数を触る場合は、thisが必要
      this.count++
    },
    decrement() {
      this.decrement_()
    },
    decrement_() {
      this.count--
    }
  },
  computed: {
    double() {
      return this.count * 2
    }
  }
}
</script>

<template>
  <!-- ここ以降で変数を触る場合はthis不要 -->
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <div class="my-wrap">
      <div>{{ title }}</div>

      <div v-if="isShow">
        <!-- hogeを値とするinputを作成 -->
        <!-- エレメントのdisabledの設定に変数isDisabledを使う -->
        <input v-model="hoge" :disabled="isDisabled"/>
        <!-- 変数hogeの値を表示する -->
        {{ hoge }}
      </div>

      <!-- clickイベントでisDisabledの値を変更する -->
      <button @click="isDisabled = !isDisabled">編集とぐる</button>

      <!-- :がないとただの文字列がclassに指定された扱い -->
      <div class="hoge">もふん</div>

      <!-- :があると変数hogeがclassに指定された扱い -->
      <div :class="hoge">もふん</div>

      <div>
        <!-- countを表示する -->
        うさぎが{{ count }}羽
        <!-- methodのincrementを実行する -->
        <button @click="increment">+1</button>
        <button @mouseover="decrement">-1</button>
      </div>

      <!-- computedのdouble()を実行した結果を表示する -->
      <div>ハムスターが{{ double }}匹</div>

      <!-- 各イベントを契機にjavascriptを実行、thisは省略 -->
      <button @mouseenter="visible = true" @mouseleave="visible = false">ひみつ</button>
      <div v-if="visible">クラスのみんなには内緒だよ</div>
    </div>

      <nav>
        <RouterLink v-for="(item, key) in pages" :key="item" :to="key">{{ item }}</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.mofumofu {
  background-color: rgb(178, 150, 73);
}

.my-wrap {
  display:flex;
  flex-flow: column;
  max-width: 300px;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
