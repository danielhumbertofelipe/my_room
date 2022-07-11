<template>
    <div class="container">
        <h3 class="info">Informações do curso</h3>
        <ul>
            <li>Professor: {{ teacher}}</li>
            <li>Sala: {{ classroom }}</li>
            <li>Bloco: {{ block }}</li>
            <li class="schedules">Horários: 
                <ul>
                    <li v-for="time in schedules">{{ time }}</li>
                </ul>
            </li>
            <li>Período: {{ period }}</li>
        </ul>
        <button @click="SeeStudents">{{ buttonStudents }}</button>
        <ul class="students" v-show="show">
            <li v-for="student in students">{{ student }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "CardInfo",
    data() {
        return {
            show: false,
            buttonStudents: "Ver alunos"
        };
    },
    props:["id", "teacher", "classroom", "block", "schedules", "period", "students"],
    methods: {
        SeeStudents() {
            this.show = !this.show;
            if(this.buttonStudents === "Ver alunos"){
                this.buttonStudents = "Ocultar alunos"
            }else{
                this.buttonStudents = "Ver alunos"
            }
        }
    }     
}
</script>

<style scoped>
    .container{
        color: #001f60;
        display: flex;
        flex-flow: column wrap;   
        align-items: center;
        max-width: fit-content;     
    }
    li {
        list-style: none;
    }
    .students {
        display: flex;
        flex-flow: row wrap;
        align-items: stretch;
        gap: 10px;
    }
    .students li{
        background-color: #d0d0ff;
        border-radius: 20px;
        padding: 2px;
    }
    ul{
        display: flex;
        flex-flow: column wrap;
        align-items: start; 
    }
    .schedules{
        display: flex;
    }
    .schedules ul{
        padding-left: 5px;
    }
</style>