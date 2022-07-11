<template>
    <div class="container">
        <div class="card" v-for="course in courses" @click="getCourses">
            <Card @click="SeeCardInfo" :coursename="course.name" :srcimage="course.srcimage"/>
            <button v-show="showCardInfo" @click="deleteCourse(course.id)">Desistir/Remover</button>
            <CardInfo v-show="showCardInfo" :teacher="course.teacher" :classroom="course.classroom" :block="course.block" :schedules="course.schedules" :period="course.period" :students="course.students" />
        </div>
    </div>
</template>

<script>
import Card from '../components/Card.vue';
import CardInfo from '../components/CardInfo.vue';
    export default {
    name: "SubsView",
    data() {
        return {
            showCardInfo: false,
            courses: null
        }
    },
    components: { 
        Card,
        CardInfo
    },
    methods: {
        SeeCardInfo() {
            this.showCardInfo = !this.showCardInfo
            
        },
        async getCourses() {
            const req = await fetch('http://localhost:3000/courses')
            const data = await req.json()
            this.courses = data
        },
            async deleteCourse(id) {
            const req = await fetch(`http://localhost:3000/courses/${id}`, {
                method: "DELETE"
            });
            const res = await req.json()
            this.getCourses()
        }
    },
    mounted() {
        this.getCourses()
    }
}
</script>

<style scoped>
    .container{
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
    }
    .card{
        margin: 5px;

    }
</style>