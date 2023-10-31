<template>
  <div class="select">
    <div class="brand">
      <h5>Бренд</h5>
      <select v-model="brandValue" :class="brandSelectColor">
        <option> ASUS </option>
        <option> Acer </option>
        <option> Lenovo </option>
        <option> HP </option>
      </select>
    </div>
    <div class="seller">
      <h5>Продавець</h5>
      <select v-model="sellerValue" :class="sellerSelectColor">
        <option> Розетка </option>
        <option> Інший продавець </option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductsFilters",
  props: {
	brand: {
      type: String,
      default: "",
    },
	 brandModifiers:{
		default: ()=>({})
	 },
	 seller: {
      type: String,
      default: "",
    },
	 sellerModifiers:{
		default: ()=>({})
	 },
  },
  data() {
	return {
		brandSelectColor: "select-color",
		sellerSelectColor: "select-color",
	}
  },
  computed: {
	brandValue:{
		get(){
			return this.brand
		},
		set(val){
			if(this.brandModifiers.check){
				this.brandSelectColor = null
			}
			this.$emit('update:brand', val)
		}
	},
	sellerValue:{
		get(){
			return this.seller
		},
		set(val){
			if(this.sellerModifiers.check){
				this.sellerSelectColor = null
			}
			this.$emit('update:seller', val)
		}
	}
  },
};
</script>

<style lang="scss" scoped></style>
