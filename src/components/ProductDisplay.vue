<template>
  <div class="container1">
    <div class="productImage">
      <img :src="image" class="productImage">
    </div>
    <div class="container-detail">
      <p class="productNameMen" v-if="category === men">{{ title }}</p>
      <p class="productNameWomen" v-else-if="category === women">{{ title }}</p>
      <div class="category-rating">
        <p class="category">{{ category }}</p>
        <div class="rating">
          <p class="ratingText">{{ rating }}/5</p>
          <div :class="{'circle-true-rating-men': rating > 0 && category === men, 'circle-true-rating-women': rating > 0 && category === women, 'circle-false-rating-men': rating <= 0 && category === men, 'circle-false-rating-women': rating <= 0 && category === women}"></div>
          <div :class="{'circle-true-rating-men': rating >= 1 && category === men, 'circle-true-rating-women': rating >= 1 && category === women, 'circle-false-rating-men': rating < 1 && category === men, 'circle-false-rating-women': rating < 1 && category === women}"></div>
          <div :class="{'circle-true-rating-men': rating >= 2 && category === men, 'circle-true-rating-women': rating >= 2 && category === women, 'circle-false-rating-men': rating < 2 && category === men, 'circle-false-rating-women': rating < 2 && category === women}"></div>
          <div :class="{'circle-true-rating-men': rating >= 3 && category === men, 'circle-true-rating-women': rating >= 3 && category === women, 'circle-false-rating-men': rating < 3 && category === men, 'circle-false-rating-women': rating < 3 && category === women}"></div>
          <div :class="{'circle-true-rating-men': rating > 4 && category === men, 'circle-true-rating-women': rating > 4 && category === women, 'circle-false-rating-men': rating < 4 && category === men, 'circle-false-rating-women': rating < 4 && category === women}"></div>
        </div>
      </div>
      <hr class="devider">
      <p class="description">{{ description }}</p>
      <hr class="devider2">
      <div class="price-button">
        <p :class="{'priceMen': category === men, 'priceWomen': category === women}" >${{ price }}</p>
        <div class="button">
          <button :class="{'button1Men': category === men, 'button1Women': category === women}">Buy now</button>
          <button @click="$emit('clickedNew')" :class="{'button2Men': category === men, 'button2Women': category === women}">Next product</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductDisplay',
  props:{
    men: String,
    women: String,
    title: String,
    rating: String,
    price: String,
    category: String,
    description: String,
    image: String,
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

.container1 {
  position: absolute;
  display: flex;
  flex-direction: row;
  top: 30%;
  width: 1034px;
  min-height: 580px;
  max-height: fit-content;
  background-color: white;
  border-radius: 15px;
  box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.25);
  align-items: center;
  justify-content: center;
  padding-top: 20px;
  padding-bottom: 20px;
}

.productImage{
  width: 306px;
  height: 407px;
  margin-left: auto;
  margin-right: 56px;
}

.container-detail{
  width: 548px;
  min-height: 484px;
  margin-right: 56px;
  display: flex;
  flex-direction: column;
  max-height: fit-content;
}

.productNameWomen{
  font-family: "Inter", sans-serif;
  font-size: 28px;
  font-weight: 600;
  font-style: normal;
  color: #720060;
  margin: 0px;
}

.productNameMen{
    font-family: "Inter", sans-serif;
    font-size: 28px;
    font-weight: 600;
    font-style: normal;
    color: #002772;
    margin: 0px;
  }

.category-rating{
  height: fit-content;
  display: flex;
  flex-direction: row;
  margin-top: 25px;
  align-items: center;
}

.category{
  margin: 0px auto 0px 0px;
  font-family: "Inter", sans-serif;
  font-size: 18px;
  font-weight: 400;
  font-style: normal;
}

.rating{
  width: fit-content;
  height: fit-content;
  display: flex;
  flex-direction: row;
  align-items: center;
}

.ratingText{
  margin: 0px 5px 0px 0px;
  font-family: "Inter", sans-serif;
  font-size: 18px;
  font-weight: 400;
  font-style: normal;
}

.circle-true-rating-women{
  width: 18px;
  height: 18px;
  border-radius: 100%;
  background-color: #720060;
  margin-right: 2px;
}

.circle-false-rating-women{
  width: 18px;
  height: 18px;
  border-radius: 100%;
  border: 1px solid #720060;
  margin-right: 2px;
}

.circle-true-rating-men{
  width: 18px;
  height: 18px;
  border-radius: 100%;
  background-color: #002772;
  margin-right: 2px;
}

.circle-false-rating-men{
  width: 18px;
  height: 18px;
  border-radius: 100%;
  border: 1px solid #002772;
  margin-right: 2px;
}

.devider{
  border-bottom: 1px solid rgba(0, 0, 0, 0.20);
  width: 542px;
}

.devider2{
  border-bottom: 1px solid rgba(0, 0, 0, 0.20);
  width: 542px;
  margin-top: auto;
}

.description{
  margin: 26px 0px 0px 0px;
  font-family: "Inter", sans-serif;
  font-size: 20px;
  font-weight: 400;
  font-style: normal;
}

.priceMen{
    font-family: "Inter", sans-serif;
    font-size: 28px;
    font-weight: 600;
    font-style: normal;
    color: #002772;
    margin: 0px;
  }

.priceWomen{
  font-family: "Inter", sans-serif;
  font-size: 28px;
  font-weight: 600;
  font-style: normal;
  color: #720060;
  margin: 0px;
}

.button{
  margin-top:15px;
  display: flex;
  flex-direction: row;
}

.button1Women{
  width: 259px;
  height: 42px;
  background-color: #720060;
  font-family: "Inter", sans-serif;
  font-size: 20px;
  font-weight: 600;
  font-style: normal;
  color: white;
  margin: 0px;
  border-radius: 4px;
}

.button2Women{
  margin-left: 20px;
  width: 259px;
  height: 42px;
  background-color: white;
  font-family: "Inter", sans-serif;
  font-size: 20px;
  font-weight: 600;
  font-style: normal;
  color: #720060;
  border-radius: 4px;
  border-color: #720060;
  border-width: 3px;
}

.button1Men{
    width: 259px;
    height: 42px;
    background-color: #002772;
    font-family: "Inter", sans-serif;
    font-size: 20px;
    font-weight: 600;
    font-style: normal;
    color: white;
    margin: 0px;
    border-radius: 4px;
  }
  
  .button2Men{
    margin-left: 20px;
    width: 259px;
    height: 42px;
    background-color: white;
    font-family: "Inter", sans-serif;
    font-size: 20px;
    font-weight: 600;
    font-style: normal;
    color: #002772;
    border-radius: 4px;
    border-color: #002772;
    border-width: 3px;
  }
</style>
