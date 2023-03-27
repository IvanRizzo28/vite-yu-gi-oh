<script>
import {store} from "../store.js";
import AppCard from './AppCard.vue';
import AppLoader from './AppLoader.vue';

export default{
    name: "Main",
    components:{
        AppCard,
        AppLoader
    },
    data(){
        return {
            store
        }
    }
}
</script>

<template>
  <main>
    <div class="container">
        <select name="tipo" id="tipo">
            <option value="alien">Alien</option>
        </select>
        <section v-if="store.n > 0">
            <div class="card-number">
                Found {{store.n}} Card
            </div>
            <div class="content">
                <div class="col" v-for="element in store.carte">
                    <AppCard 
                    :img="element.card_images[0].image_url"
                    :text="element.name"
                    :tipo="element.archetype"
                    />
                </div>
            </div>
        </section>
        <section v-else>
            <AppLoader />
        </section>
    </div>
  </main>
</template>

<style scoped lang="scss">
@use '../assets/stili/container.scss' as *;
@use '../assets/stili/mixin.scss' as *;
main{
    padding: 1.25rem;
}
select{
    padding: .625rem 2.5rem .625rem .625rem;
}
section{
    padding: 1.25rem;
    background-color: #fff;
    margin-top: 1.25rem;
    .card-number{
        padding: .625rem;
        background-color: #444864;
    }
    .content{
        @include flexWrap;
        overflow-y: auto;
        .col{
            width: calc(100% / 5);
            padding: 1.25rem .625rem;
        }
    }
}
</style>