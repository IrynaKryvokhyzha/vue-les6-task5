<template>
	<div class="page-container">
		<products-filters 
		v-model:brand.check="notebookBrand"
		v-model:seller.check="notebookSeller" />
		
		<products-panel :cards-list-data="filteredNotebooksList" />	
	</div>
</template>

<script>
import ProductsFilters from "./components/ProductsFilters.vue";
import ProductsPanel from "./components/ProductsPanel.vue";
import { notebooksList } from "./constants/notebooks_data";
export default {
  name: "App",

  components: {
    ProductsPanel,
    ProductsFilters,
  },

  data() {
    return {
      notebooksList,
		notebookBrand: null,
		notebookSeller: null
    };
  },

  computed: {
	filteredNotebooksList() {
		if(this.notebookBrand || this.notebookSeller){
			return notebooksList.filter((notebook)=>this.ifNotebookMatches(notebook))
		}
		return notebooksList 
	}
  },
  methods: {
	ifNotebookMatches(notebook) {
		return (
			(!this.notebookBrand || notebook.brand ===this.notebookBrand ) &&
		(!this.notebookSeller || notebook.seller === this.notebookSeller)
		)
	}
  },
};
</script>

<style lang="scss">
@import "./assets/style";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
