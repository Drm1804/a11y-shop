<template>
  <div class="card">
    <h3>{{ title }}</h3>

    <div class="description">
      <img :src="require(`../assets/${image}.jpeg`)" :alt="`Изображение товара ${title}`" />

      <div class="text">
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Delectus ut
          numquam quam culpa similique, deleniti omnis minima adipisci
          voluptatibus ad, consequatur sunt temporibus neque quo sit accusantium
          earum. Corporis, dolorum!
        </p>

        <button @click="add($event)">
          Добавить<span class="sc-only"> {{ title }}</span> в корзину
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    image: String,
    title: String,
  },
  methods: {
    add(event) {
      this.$emit('click', event)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  border: 1px solid grey;
  padding: 4px 8px;
  border-radius: 8px;
  max-width: 600px;
  margin: 8px;
}

.description {
  display: flex;
  text-align: left;
}

.sc-only {
  width: 0;
  height: 1px;
  overflow: hidden;
  display: inline-flex;
}

img {
  max-width: 200px;
  margin-bottom: 24px;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
