<template>
  <div id="app">
    <div v-if="isLoading" class="background" style="background-color: #D8D7D7">
      <LoadingView v-if="isLoading"/>
    </div>
    <div v-if="category === men && isLoading == false" class="background" style="background-color: #D6E6FF">
      <ProductDisplay class="container" :men="men" :women="women" :title="title" :rating="rating" :price="price" :category="category" :description="description" :image="image" @clickedNew="nextProduct()"/>
  </div>
  <div v-else-if="category === women && isLoading == false" class="background" style="background-color: #FDE2FF">
      <ProductDisplay class="container" :men="men" :women="women" :title="title" :rating="rating" :price="price" :category="category" :description="description" :image="image" @clickedNew="nextProduct()"/>
  </div>
  <div v-else-if="(category !== men || category !== women) && isLoading == false" class="background" style="background-color: #D8D7D7">
      <NoProductDisplay class="container" @clickedNew="nextProduct()"/>
  </div>
  </div>
</template>

<script>
import NoProductDisplay from '/components/NoProdutDisplay.vue';
import ProductDisplay from '/components/ProductDisplay.vue';
import LoadingView from '/components/LoadingView.vue';

export default {
  name: 'App',
  components: {
    ProductDisplay,
    NoProductDisplay,
    LoadingView,
  },
  data(){
    return{
      men: "men's clothing",
      women: "women's clothing",
      end: false,
      id: null,
      title: null,
      rating: null,
      price: null,
      category: null,
      description: null,
      image: null,
      number: 0,
      isLoading: true,
    };
  },
  methods:{
    async getProductFromAPI(){
      this.setLoading()
      const api = await fetch('https://fakestoreapi.com/products/')
      const response = await api.json()
      this.id = response[this.number].id
      this.title = response[this.number].title
      this.price = response[this.number].price
      this.category = response[this.number].category
      this.description = response[this.number].description
      this.image = response[this.number].image
      this.rating = response[this.number].rating.rate;
      this.stopLoading()
    },

    nextProduct(){
      this.number += 1
      if(this.number === 20){
        this.number = 0
      } else {
      this.getProductFromAPI();
      }
    },

    setLoading(){
      this.isLoading = true;
    },

    stopLoading(){
      this.isLoading = false;
    }
  },
    
  mounted(){
    this.getProductFromAPI()
  }
};
</script>

<style>
body, html {
    margin:0;
    padding:0;  
}

#app {
    height: 100vh;
    width: 100vw;
    padding: 0px;
    margin: 0px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .background{
    display: flex;
    justify-content: center;
    position: absolute;
    top: 0px;
    width: 100vw;
    height: 584px;
}
</style>
