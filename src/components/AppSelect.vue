<script>
import axios from 'axios';
import { store } from "../store";
export default {
    name: 'Select',
    data(){
        return{
            arr:[],
            store
        }
    },
    methods: {
        getArchetype() {
            axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then((response) => {
                //console.log(response.data);
                this.arr=response.data;
                console.log(this.arr);
            });
        }
    },
    created(){
        this.getArchetype();
    }
}
</script>

<template>
    <select name="tipo" id="tipo" v-model="store.cerca" @change="$emit('search')">
        <option value="">Select archetype</option>
        <option :value="element.archetype_name" v-for="element in arr">{{ element.archetype_name }}</option>
    </select>
</template>

<style scoped>
select {
    padding: .625rem 2.5rem .625rem .625rem;
}
</style>