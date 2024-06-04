<script>
import AppCard from "./AppCard.vue";

export default {
    components: {
        AppCard,
    },
    props: {
        cardsArray: Array,
    },
    data() {
        return {

            currentPage: 1,
            itemsPerPage: 10,
        };
    },
    computed: {
        paginatedData() {
            const start = (this.currentPage - 1) * this.itemsPerPage;
            const end = start + this.itemsPerPage;
            return this.cardsArray.slice(start, end);
        },
        isFirstPage() {
            return this.currentPage === 1;
        },
        isLastPage() {
            return this.currentPage * this.itemsPerPage >= this.cardsArray.length;
            
        },
    },
    methods: {
        nextPage() {
            if (!this.isLastPage) {
                this.currentPage++;
            }
        },
        prevPage() {
            if (!this.isFirstPage) {

                this.currentPage--;

            }
        },
    },
};
</script>

<template>
  <div class="container bg-light">
    <div class="row">
      <div class="col-12 col-md-6 col-lg-4" v-for="card in paginatedData" :key="card.id">
        <AppCard :cardObj="card" />
      </div>
    </div>
    <div class="row">
      <div class="col-12 d-flex justify-content-between mt-3">
        <button class="btn btn-primary" @click="prevPage" :disabled="isFirstPage">Previous</button>
        <button class="btn btn-primary" @click="nextPage" :disabled="isLastPage">Next</button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
body {
  background-color: #f5f5f5; 
}

.card {
  background-color: #fff; 
  border: 1px solid #ddd; 
  border-radius: 0.25rem;
}

.btn-primary {
  background-color: #007bff; 
  border-color: #007bff; 
}
</style>