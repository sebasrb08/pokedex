<template>
  <div class="conten2">
    <div class="titulo">
      <h1>{{ nombre }}</h1>
    </div>
    <div class="info">
        <div class="info__imagen">
          <img :src="urll" alt="">
        </div>
        <div class="info__texto">
          <div class="stats">
              <h4 class="stats__title">stats</h4>
              <div>
                <p v-for="i in response.stats " :key= "i.name" class="stats__text" >{{ i.stat.name}} :<span>{{i.base_stat}} </span></p>
               
              </div>
          </div>
          <div class="abilities">
            <h4 class="stats__title">abilities</h4>
            <div>
              <p class="stats__text" v-for="i in response.abilities" :key="i.name">{{ i.ability.name }}</p>
            </div>
          </div>
        </div>
    </div>
    <div class="pictures">
      <div class="pictures__title">
          <h4 class="pictures__title--big">Pictures</h4>
      </div>
      <div class="pictures__img">
          <div class="pictures__imgC"><img :src="sprite.back_default" alt=""></div>
          <div class="pictures__imgC"><img :src="sprite.back_shiny" alt=""></div>
          <div class="pictures__imgC"><img :src="sprite.front_default" alt=""></div>
          <div class="pictures__imgC"><img :src="sprite.front_shiny" alt=""></div>
      </div>
    </div>
  </div>
</template>


<script>
import { onMounted } from 'vue';

export default{
  name:"PokemonPage",
  data(){
    return{
      response:[],
      nombre:this.$route.params.pokeapi2,
      urll:"",
      sprite:{}
    }

  },
  mounted(){
    console.log(this.$route)
    this.getInfo()
  },
  methods:{
    async getInfo(){
          const {data} = await this.$axios.get(`pokemon${this.$route.fullPath}`)
          this.response=(data)
          console.log(this.response)
          this.urll=this.response.sprites.other.dream_world.front_default
          this.sprite=this.response.sprites

        },
  }
}


</script>


<style>
.conten2{
  height: 100%;
  width: 100%;
  background-color: rgb(133, 174, 250);
  padding: 20px;
}
.titulo{
  height: 20%;
  width: 100%;
  background-color: rgba(245, 116, 30, 0.836);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;
  color: black;
  box-shadow: 0px 10px 10px black;
  font-weight: 800;

}
.info{
  display: flex;
  margin-top: 20px;
}
.info__imagen{
  width: 30%;
  height: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.info__texto{

  width: 70%;
  height: 50%;
  display: flex;
  border: rgb(77, 77, 77) 4px solid;
  border-radius: 10px;
  box-shadow: 0px 10px 10px black;

}
.stats{
  width: 50%;
}
.abilities{
  width: 50%;

}
.stats__title{
  font-size: 50px;
}
.stats__text{
  font-size: 30px;
}
.pictures{
  height: 50%;
  margin-top: 25px;

}
.pictures__title{
  height: 20%;
  width: 100%;
  background-color: rgba(245, 116, 30, 0.836);
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0px 10px 10px black;


}
.pictures__title--big{
  font-size: 60px;
  color: white;
  font-weight: 800;

}
.pictures__img{
  display: flex;
  gap: 20px;
}
.pictures__imgC{
  width: 25%;
  height: 80%;
  display: flex;
  justify-content: center;
  }
</style>