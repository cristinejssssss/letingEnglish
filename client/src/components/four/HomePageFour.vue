<template>
<div class="homepagefour">
    <h1>四级听力</h1>
    <ul class="homepagefour1">
      <li v-if="count" v-for="(item,index) in count">
          <router-link  :to="`/four/${item}`">
            <svg class="icon" aria-hidden="true">
                <use xlink:href="#icon-rili"></use>
            </svg>
            <p class="day">day{{item}}</p>
          </router-link>
    </li>
    </ul>
</div>
 
</template>

<script>
export default {
        name: 'HomePageFour',
        data() {
            return {
                count:""
            };
        },
        created(){
            this.getCount();
        },
        methods:{
            getCount(){
                this.$axios.get("http://localhost:5000/api/listen/four/count")
                .then(res => {
                    this.count = res.data;
                }).catch(err => {
                    console.log(err.response);
                });
            }
        }
       
}
</script>

<style scoped>
.icon {
   width: 3em; height: 3em;
   vertical-align: -0.15em;
   fill: currentColor;
   overflow: hidden;
   margin-bottom: 10px;
}

.homepagefour{
     text-align: center;
}
    .homepagefour1{
      margin: 20px auto;
      width:80%;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      -ms-flex-pack:distribute;
          justify-content:space-around;
      -ms-flex-wrap: wrap;
          flex-wrap: wrap;
    }

    .homepagefour1 li{
     font-size:23px;
      padding:20px;
      border:3px solid #DF5048;
      width:16%;
      height:160px;
      margin:40px;
      text-align: center;
      border-radius: 20px;
      -webkit-box-shadow: 8px 8px 8px #ccc;
              box-shadow: 8px 8px 8px #ccc;
      opacity: 0.8;
       -webkit-transition: all 0.2s ease;
       transition: all 0.2s ease;
    }

    .homepagefour1 li:hover{
      -webkit-transform: translate(5px,5px);
              transform: translate(5px,5px);
    }


    
@media(max-width:480px){
.icon {
   width: 2em; height: 2em;
   vertical-align: -0.15em;
   fill: currentColor;
   overflow: hidden;
   margin-bottom: 10px;
}

 .homepagefour1 li{
      padding:10px;
      border:3px solid #DF5048;
      width:16%;
      height:160px;
      margin:20px;
      text-align: center;
      border-radius: 20px;
      -webkit-box-shadow: 8px 8px 8px #ccc;
              box-shadow: 8px 8px 8px #ccc;
      opacity: 0.8;
       -webkit-transition: all 0.2s ease;
       transition: all 0.2s ease;
    }
}

</style>
