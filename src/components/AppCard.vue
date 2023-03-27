<script>
import { def } from '@vue/shared';

export default{
    name: "card",
    props:{
        img: String,
        text: String,
        tipo: String
    }
}
</script>

<template>
    <div class="card">
        <div>
            <img :src="img" :alt="text">
        </div>
        <h3>{{text}}</h3>
        <p>{{tipo}}</p>
    </div>
</template>

<style scoped lang="scss">
    .card{
        text-align: center;
        background-color: #d48f38;
        padding-bottom: .625rem;
        height: 100%;
    }
    img{
        width: 100%;
    }
    h3{
        color: #fff;
        margin: .625rem 0;
    }
</style>