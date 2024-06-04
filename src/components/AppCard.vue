<script>
export default {
    props: {
        cardObj: Object,
        
    },
    data() {
        return {
            
        };
    },
    
};
</script>

<template>
  <div class="card p-3 mt-5">
    <img :src="cardObj.image" class="card-img-top rounded-circle" alt="Character Image">
    <div class="card-body">
      <h5 class="card-title">{{ cardObj.name }}</h5>
      <p class="card-text">{{ cardObj.species }}</p>
      <p class="card-text">{{ cardObj.status }}</p>
    </div>
  </div>
</template>


<style lang="scss" scoped>
.infos {
    & h4 {
        font-size: 30px;
    }

    & p {
        font-size: 20px;
    }
}
img {
    width: 100%;
}
</style>