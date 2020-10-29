<template>
  <div id="appC">
    @{{ user.userName }} {{ getFullName }}
    <br/><br/>
    Followers: <strong>{{ followers }}</strong>
    <br/><br/>
    <button @click="FollowUser">Follow</button>
    <div class="m-t-10">
    <ul class="p-0">
        <dd class="p-0" v-for="product in products" :key="product._id">{{product.title}}</dd>
    </ul>
    </div>
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
      products: {}
    };
  },
  computed: {
    getFullName(){
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  watch:{
    followers(newCount,oldCount){
      console.log(newCount,oldCount);
    },
    products(){
      this.$forceUpdate();
      console.log(this.products);
    }
  },
  methods: {
    FollowUser(){
      this.followers++;
    },
    async getAllProducts(){
      await fetch("http://localhost:3000/posts/getAllProducts").then(response => response.json())
  .then(data => {console.log(data);this.products = data;});
    }
  },
  mounted(){
    this.followers = 5;
    this.getAllProducts();
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
.p-0{
  padding: 0%;
  margin: 0%;
}
.m-t-10{
  margin-top: 10px;
}
</style>
