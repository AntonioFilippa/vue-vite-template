<script>
import { store } from "../store";
export default {
    data() {
        return {
            store,
            options: ["All", "Alive", "Dead", "unknown"],
        };
    },
};
</script>

<template>
    <div class="container py-4">
        <div class="d-flex justify-content-between">
            <div>
                <select class="form-select" @change="$emit('filter')" v-model="store.selectedStatus">
                    
                    <option :value="state" v-for="state in options" :key="state">
                        
                        {{ state }}
                    </option>
                </select>
               
            </div>
        </div>
    </div>
</template>