<script>
import { store } from "./store";
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";
import AppSearch from "./components/AppSearch.vue";
import AppCard from "./components/AppCard.vue";

export default {
    components: {
        AppHeader,
        CardsList,
        AppSearch,
        AppCard
    },
 
    data() {
        return {
            store,
            cardsArray: [],
            
        };
    },
    created() {
        this.getStatus();
    },
    
 

    
    
    
    
    methods: {
        reset() {
            this.store.selectedStatus = "All";
            this.getStatus();
        },
  
                 getStatus() {
                     console.log("Get Status", this.store.selectedStatus);
                     
                     if (this.store.selectedStatus !== "All") {
                         axios
                         .get("https://rickandmortyapi.com/api/character", {
                             params: {
                                 status: this.store.selectedStatus
                                }
                            })
                            .then((resp) => {
                                this.cardsArray = resp.data.results;
                            })
                        } else {
                            axios
                            .get("https://rickandmortyapi.com/api/character")
                            .then((resp) => {
                                this.cardsArray = resp.data.results;
                            })
                        }
                    },
      
    },
};
</script>

<template>
    <div class="test">
        <AppHeader @reset="reset" />
        <AppSearch @filter="getStatus" />
        <CardsList :cardsArray="cardsArray" />
    </div>
</template>

<style lang="scss" scoped>
.test {
    
    background-position: center;
    background-size: contain;
    background-repeat: no-repeat;
}
</style>