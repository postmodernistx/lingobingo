<template>
  <main>
    <h1>Lingo Bingo</h1>
    <p>Klicka/space för att markera en bricka</p>
    <div class="board">
      <CellButton :word="item" v-for="(item, index) in words" :key="`word-${index}`" />
    </div>
  </main>
</template>

<script>
import CellButton from '@/components/Cell.vue';

export default {
  name: 'App',
  components: { CellButton },
  data() {
    return {
      words: ['Lighthouse', 'Primary color', 'sans-serif', 'SEO', 'graphic profile',
        'secondary color', 'color wheel', 'UI/UX', 'gitmoji', 'React',
        'Vue', 'Sass', 'Illustrator', 'Photoshop', 'Figma',
        'pull request', 'API', 'a11y', 'Internet Explorer', 'WordPress',
        'Heroku', 'HTML', 'router', 'responsive', 'agile',
      ],
    };
  },
  methods: {
    shuffle(array) {
      let currentIndex = array.length;
      let randomIndex;

      while (currentIndex !== 0) {
        randomIndex = Math.floor(Math.random() * currentIndex);
        // eslint-disable-next-line no-plusplus
        currentIndex--;

        // And swap it with the current element.
        // eslint-disable-next-line no-param-reassign
        [array[currentIndex], array[randomIndex]] = [
          array[randomIndex], array[currentIndex]];
      }

      return array;
    },
  },
  mounted() {
    this.words = this.shuffle(this.words);
  },
};
</script>

<style lang="scss">
* { box-sizing: border-box }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  font-family: 'Rock 3D', cursive;
  font-size: 8rem;
  margin: 0;
  line-height: 1.2;
  background-image: linear-gradient(to left,
      #0dc4b7,
      #9a2654,
      #2a47d5,
      #19d519,
      #e9ff00,
      #ff8000,
      #f30a0a
  );
  -webkit-background-clip: text;
  color: transparent;
}
.board {
  margin: 30px auto;
  border: 3px solid black;
  padding: 15px;
  border-radius: 5px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  gap: 20px;
  width: 140 * 5px;
}
</style>
