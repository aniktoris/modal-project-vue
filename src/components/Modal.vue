<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{sale: theme === 'sale'}">
      <slot></slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: ['theme'],
  methods: {
    closeModal(){
      this.$emit('close')
    }
  }
}
</script>


<style>
.modal{
  background: white;
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  border-radius: 10px;
}

.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}

.modal .actions a {
  color: #333;
  padding: 8px;
  border: 2px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.modal .backdrop {
  top: 0;
  background: rgba(0,0,0,0.5);
  width: 100%;
  height: 100%;
  position: fixed;
}

h1{
  color: orange;
  border: none;
  padding: 0;
}

.modal.sale {
  background: crimson;
  color: white;
}

.modal.sale h1 {
  color: white;
}

.modal.sale .actions {
  color: white;
}

.modal.sale .actions a {
  color: white;
}

</style>