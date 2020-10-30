<template>
  <nav-bar @change-component="updateSelectedComponent"></nav-bar>
  <keep-alive>
    <component :is="selectedComponent" v-bind="currentProps" @update-selection="updateSelection" @update-selection2="updateSelection2"></component>
  </keep-alive>

</template>

<script>
import MotoList from "./components/MotoList";
import NavBar from "./components/navigation/NavBar";
import SelectionList from "./components/SelectionList";
import accSelectionList from "./components/accSelectionList";

export default {
  name: 'App',
  components: {
    MotoList,
    NavBar,
    SelectionList,
    accSelectionList
  },
  data(){
    return {
      selectedComponent: 'moto-list',
      selectionArray: [],
      selectionArray2: []
    }
  },
  computed: {
    currentProps() {
      if(this.selectedComponent == "selection-list") {
        return { selection: this.selectionArray }
      }else if(this.selectedComponent == "acc-selection-list") {
        return { selection2: this.selectionArray2 }
      }
      return false
    }
  },
  methods: {
    updateSelectedComponent(comp) {
      this.selectedComponent = comp
    },
    updateSelection(moto) {
      this.selectionArray.push(moto)

    },
    updateSelection2(acc) {
      this.selectionArray2.push(acc)

    }
  }
}
</script>

<style>

</style>
