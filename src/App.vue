<template>
  <div id="app">
    <VDropdown v-slot="{ show, toggleFn }">
      <button @click="toggleFn">Toggle</button>
      <VDropdownMenu :show="show"></VDropdownMenu>
    </VDropdown>
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
