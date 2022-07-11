<template>
  <div>
    <UserInfo :user="user"/>
  </div>
</template>

<script>
import UserInfo from '../components/UserInfo.vue'
export default {
  name: 'HomeView',
  data() {
    return {
      user: null
    }
  },
  components: {
    UserInfo
  },
  methods: {
    async getUser(id) {
      const req = await fetch(`http://localhost:3000/users/${id}`)
      const data = await req.json();
      this.user = data;
    }
  },
  beforeMount() {
    this.getUser("1");
  }
}
</script>
