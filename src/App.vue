<template>
  <div id="app">
    <div class="center">
      <VDropdown v-slot="{ show, toggleFn }">
        <VDropdownItem tag="button" @click="toggleFn">TOGGLE</VDropdownItem>

        <VDropdownMenu align-right :show="show" @onclose="toggleFn">
          <VDropdownItem>Hola</VDropdownItem>
          <VDropdownItem>Mundo</VDropdownItem>

          <VDropdown v-slot="sub">
            <VDropdownItem @click="sub.toggleFn">Toggle Func</VDropdownItem>
            <VDropdownMenu
              submenu
              align-right
              :show="sub.show"
              @onclose="sub.toggleFn"
            >
              <VDropdownItem>HolaC</VDropdownItem>
              <VDropdownItem>MundoC</VDropdownItem>
              <VDropdownItem>MundialC</VDropdownItem>
            </VDropdownMenu>
          </VDropdown>

          <VDropdownItem>Mundial</VDropdownItem>
        </VDropdownMenu>
      </VDropdown>
    </div>
  </div>
</template>

<script>
import VDropdown from './components/VDropdown.vue';
import VDropdownMenu from './components/VDropdownMenu.vue';
import VDropdownItem from './components/VDropdownItem.vue';

export default {
  name: 'App',
  components: {
    VDropdown,
    VDropdownMenu,
    VDropdownItem,
  },

  methods: {
    onClose() {
      console.log('received');
    },
  },
};
</script>

<style>
.center {
  display: flex;
  justify-content: center;
}
</style>
