<template>
  <div id="appC">
    @{{ user.userName }} {{ getFullName }}
    <br/><br/>
    Followers: <strong>{{ followers }}</strong>
    <br/><br/>
    <button @click="FollowUser">Follow</button>
  </div>  
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      isLoading: false,
      followers: 0,
      user: {
        id: 1,
        userName: "ymjess",
        firstName: "Yeasin Mahmud",
        lastName: "Jesan",
        email: "ymjesanlemon@gmail.com",
        isAdmin: true,
      },
    };
  },
  computed: {
    getFullName(){
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods: {
    FollowUser(){
      this.followers++;
    }
  },
  mounted(){
    this.followers = 5;
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}
</style>
