<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name"/>
  <button @click="handleClick">click me</button>
  <teleport to=".modals" v-if="showModal">
  <Modal theme="sale" @close="toggleModal">
    <template v-slot:links>
      <a href="#">sign up now</a> |
      <a href="#">more info</a>
    </template>
    <h1>Ninja Giveaway!</h1>
    <p>Grab your ninja swag for half price!</p>
  </Modal>
  </teleport>
  <button @click.alt="toggleModal">open modal (alt)</button>
  <teleport to='.modals' v-if="!showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:links>
      <a href="#">get this new deal!</a> |
      <a href="#">contact info</a>
    </template>
      <h1>Ietsknits</h1>
      <p>Order cool sweaters and shawls now!</p>
    </Modal>
  </teleport>
  <button @click="toggleModalTwo">open second modal</button>
</template>

<script>
import Modal from './components/Modal'
export default {
  name: "App",
  components: {
    Modal
  },
  data() {
    return {
     title: 'My First Vue App :)',
     showModal: false,
     showModalTwo: false
    }
  },
  methods: {
    handleClick(){
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },
    toggleModal(){
      this.showModal = !this.showModal;
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo;
    }
  }
};
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 3px solid orange;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
