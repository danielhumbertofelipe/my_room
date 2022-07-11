<template>
    <div class="card">
        <Img class="img" :srcimage="srcimage"/>
        <div class="container">
            <p>{{ coursename }}</p>  
        </div>
    </div>
</template>

<script>
import Img from "./Img.vue";

export default {
    name: "Card",
    components: {
        Img
    },
    props: ["coursename","srcimage"]
}
</script>

<style scoped>
    .card {
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        width: 300px;
        border-radius: 25px;
        border: 2px solid aquamarine;
    }

    .card:hover {
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
        cursor: pointer;
    }

    .img {
        border-radius: 25px 25px 0 0;
        height: 150px;
    }

    .container {
        padding: 1px 16px;
        background-color: #d0d0ff;
        color: #001f60;
        border-radius: 0px 0px 25px 25px;
        font-weight: bold;
    }
</style>