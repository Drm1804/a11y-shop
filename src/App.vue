<template>
  <div id="app">
    <Title title="Super shop" />
    <div class="wrap">
      <Card
        v-for="c in cards"
        :key="c.id"
        v-on:click="openModal(c.id, $event)"
        :image="c.id"
        :title="c.title"
      />
    </div>
    <Modal v-if="isModelShow" :title="getTitle" @close="closeModal" />
  </div>
</template>

<script>
import Card from "./components/card.vue";
import Modal from "./components/modal.vue";
import Title from "./components/title.vue";
import "wicg-inert";

export default {
  name: "App",
  components: {
    Card,
    Modal,
    Title,
  },
  data: function () {
    return {
      selectedItem: null,
      previousFocus: null,
      isModelShow: false,
      cards: [
        {
          id: "watch1",
          title: "Часы Casio черные",
        },
        {
          id: "watch2",
          title: "Часы Q&Q желтые",
        },
        {
          id: "watch3",
          title: "Часы Слава коричневые",
        },
        {
          id: "watch4",
          title: "Часы Слава черные",
        },
        {
          id: "watch5",
          title: "Часы Casio красные",
        },
        {
          id: "watch7",
          title: "Часы спортивные",
        },
      ],
    };
  },
  computed: {
    getTitle() {
      return this.cards.find((el) => el.id === this.selectedItem).title;
    },
  },
  methods: {
    openModal(id) {
      this.selectedItem = id;
      this.isModelShow = true;
    },
    closeModal() {
      this.isModelShow = false;
      this.previousFocus = null;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrap {
  display: flex;
  flex-wrap: wrap;
}
</style>
