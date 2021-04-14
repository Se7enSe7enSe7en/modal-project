<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal" >
      <template v-slot:links> 
        <a href="#">sign up now</a>  
        <a href="#">more info</a>
      </template>
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
      <p>{{ weird_array }}</p>  
    </Modal>
  </div>

  <div v-if="showModal2">
    <Modal theme="saled" @close="toggleModal2" >
      <h1>Modal 2</h1>
      <p>testing testing</p>
      <p>hmmmmmmm</p>  
    </Modal>
  </div>

  <button @click="toggleModal">open modal</button>
  <button @click="toggleModal2">open modal 2</button>
  
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Modal from "./components/Modal.vue"

@Options({
  components: { 
    Modal, 
  },
  data() {
    return{
      title: "My First Vue App",
      header: "Sign up for the Giveaway!",
      text: "Grab your ninja swag for half price!",
      weird_array: [2, 7, 4, 3],
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active") // [!] [class: active] is a class that adds a CSS effect when activated
      this.$refs.name.focus() // [!] [.focus()]when button is clicked it will focus the input box
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2
    },
  },
})
export default class App extends Vue {}
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
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
