<template>
    <header>
        <Logo class="logo"/>
        <div class="user">
            <span class="welcome">Bem vindo Fulano</span>
            <select name="account" @change="actionaccount($event)">
                <option selected hidden></option>
                <option value="MyAccount">Minha conta</option>
                <option value="leave">Sair</option>
            </select>
            <div class="circle"><Img /></div>
        </div>
    </header>
</template>

<script>
import Logo from './Logo.vue'
import Img from './Img.vue'
export default {
    name: "Header",
    components:{
        Logo,
        Img
    },
    methods: {
        actionaccount(event) {
            const option = event.target.value;
            if(option === "MyAccount"){
               this.$router.replace('/') 
            }else if(option === "leave"){
                this.$router.replace('login') 
            }
        }
    }
}
</script>

<style scoped>
    header{
        background-color: #001f60;
        width: 100%;
        height: 100px;
        display: flex;
        align-items: center;
        position: absolute;
        left: 0;
        top: 0;
        color: white;
    }

    .logo {
        padding-left: 20px;
        font-size: xxx-large;
    }

    .welcome {
        position: absolute;
        right: 115px;        
    }

    select {
        border: none;
        background-color: #001f60;
        position: absolute;
        right: 93px;
        width: 20px;
        color: white;     
    }

    .user{
        display: flex;
        align-items: center;
    }

    .user .circle{
        position: absolute;
        right: 20px;
    }

    .circle{
        height: 70px;
        width: 70px;
        border-radius: 50%;
        overflow: hidden;
        position: relative;
        display: flex;
        justify-content: center;
        background-color: white;
    }

    Img{
        position: relative;
        height: 100%;
    }
</style>