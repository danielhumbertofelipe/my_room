<template>
    <div class="container">
        <div class="circle"><Img /></div>
        <div class="infor">
            <p v-show="!edit">{{ user.name }}</p>
            <p v-show="!edit">{{ user.email }}</p>
            <p v-show="!edit">{{ user.phone }}</p>
            <button v-show="!edit" @click="modeEdit">Editar</button>
            <p v-show="edit">Altere os dados</p>
            <form method="POST" @submit="updateUser">
                <input v-show="edit" type="text" name="username" id="name" v-model="username" :placeholder="user.name">
                <input v-show="edit" type="text" name="email" id="email" v-model="email" :placeholder="user.email">
                <input v-show="edit" type="text" name="phone" id="phone" v-model="phone" :placeholder="user.phone"><br><br>
                <input type="button" v-show="edit" @click="modeEdit" value="Cancel">
                <input v-show="edit" type="submit" value="Save">
            </form>
        </div>
    </div>
</template>

<script>
import Img from './Img.vue'
export default {
    name: "UserInfo",
    data() {
        return{
            edit: false,
            username: null,
            email: null,
            phone: null
        }
    },
    props: {
        user: []
    },
    components: {
        Img
    },
    methods: {
        modeEdit() {
            this.edit = !this.edit
        },
        updateUser(e) {
            e.preventDefault()
            if(this.username === "" || this.username === null){
                this.username = this.user.name
            };
            if(this.email === "" || this.email === null){
                this.email = this.user.email
            };
            if(this.phone === "" || this.phone === null){
                this.phone = this.user.phone
            };
            const data = {
                username: this.username,
                email: this.email,
                phone: this.phone,
            }
            const nameJson = JSON.stringify({name: data.username});
            const emailJson = JSON.stringify({email: data.email});
            const phoneJson = JSON.stringify({phone: data.phone});
            const reqname = fetch(`http://localhost:3000/users/${this.user.id}`, {
                method: "PATCH",
                headers: { "Content-Type" : "application/json" },
                body: nameJson
            });
            const reqemail = fetch(`http://localhost:3000/users/${this.user.id}`, {
                method: "PATCH",
                headers: { "Content-Type" : "application/json" },
                body: emailJson
            });
            const reqphone = fetch(`http://localhost:3000/users/${this.user.id}`, {
                method: "PATCH",
                headers: { "Content-Type" : "application/json" },
                body: phoneJson
            });
            alert("Alterado com sucesso!")
            this.user.name = this.username
            this.user.email = this.email
            this.user.phone = this.phone
            this.modeEdit()
        }
    }
}
</script>

<style scoped>
    .container{
        color: #001f60;
        margin-left: 50px;
    }

    .circle{
        height: 170px;
        width: 170px;
        border-radius: 50%;
        overflow: hidden;
        display: flex;
        justify-content: center;
        background-color: white;
    }

    .circle:hover {
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
        cursor: pointer;
        mask-image: url("../assets/images/acima.png");
        mask-size: cover;
        mask-mode: inherit;
        opacity: 0.5;
    }

    p, button{
        display: flex;
        justify-content: start;
    }
</style>