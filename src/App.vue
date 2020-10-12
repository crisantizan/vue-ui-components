<template>
  <div id="app">
    <div class="center">
      <VDropdown v-slot="{ show, toggleFn }">
        <button @click="toggleFn">Toggle</button>
        <VDropdownMenu align-right :show="show"></VDropdownMenu>
      </VDropdown>
    </div>
  </div>  
</template>

<script>
import VDropdown from './components/VDropdown.vue';
import VDropdownMenu from './components/VDropdownMenu.vue';

export default {
  name: 'App',
  components: {
    VDropdown,
    VDropdownMenu,
  },
};
</script>

<style>
  .center {
    display: flex;
    justify-content: center;
  }
</style>
