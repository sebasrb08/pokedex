<template>
  <div class="conten2" ref="conten2">
    <div class="titulo">
      <h1 :style="{ textTransform: 'uppercase' }">{{ nombre }}</h1>
    </div>
    <div class="info">
        <div class="info__texto">
          <div class="stats">
              <h4 :style="{ textTransform: 'uppercase' }" class="stats__title">stats</h4>
              <div>
                <p :style="{ textTransform: 'uppercase' }" v-for="i in response.stats " :key= "i.name" class="stats__text" >{{ i.stat.name}}  :<span >{{i.base_stat}} </span></p>
              </div>
          </div>

          <div class="info__imagen">
            <img class="info__poke" :src="urll" alt="">
          </div>

          <div class="abilities">
            <h4 :style="{ textTransform: 'uppercase' }" class="stats__title">abilities</h4>
            <div>
              <p :style="{ textTransform: 'uppercase' }" class="stats__text" v-for="i in response.abilities" :key="i.name">{{ i.ability.name }}</p>
            </div>
          </div>
        </div>
    </div>
    <div class="pictures">
      <div class="pictures__title">
          <h4 :style="{ textTransform: 'uppercase' }" class="pictures__title--big">Pictures</h4>
      </div>
      <div class="pictures__img">
          <div class="pictures__imgC"><img class="pictures__imagen" :src="sprite.back_default" alt=""></div>
          <div class="pictures__imgC"><img class="pictures__imagen" :src="sprite.back_shiny" alt=""></div>
          <div class="pictures__imgC"><img class="pictures__imagen" :src="sprite.front_default" alt=""></div>
          <div class="pictures__imgC"><img class="pictures__imagen" :src="sprite.front_shiny" alt=""></div>
      </div>
    </div>
    
    <div class="devolver">
      <img @click="atras" class="devolver__flecha" src="/atras.svg" alt="">
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
          this.urll=this.response.sprites.other.dream_world.front_default
          this.sprite=this.response.sprites
          const conten2=this.$refs.conten2
          
          if(this.response.types[0].type.name =="fire"){
                conten2.style.backgroundColor="	rgb(240,80,48)"
            }
            if(this.response.types[0].type.name =="grass"){
                conten2.style.backgroundColor="	rgb(120,200,80)"
            }
            if(this.response.types[0].type.name =="water"){
                conten2.style.backgroundColor="	rgb(56,153,248)"
            }
            if(this.response.types[0].type.name =="normal"){
                conten2.style.backgroundColor="	rgb(168,160,144)"
            }
            if(this.response.types[0].type.name =="bug"){
                conten2.style.backgroundColor="rgb(168,184,32)"
            }
            if(this.response.types[0].type.name =="poison"){
                conten2.style.backgroundColor="	rgb(176,88,160)"
            }
            if(this.response.types[0].type.name =="electric"){
                conten2.style.backgroundColor="		rgb(248,208,48)"
            }
            if(this.response.types[0].type.name =="rock"){
                conten2.style.backgroundColor="		rgb(184,160,88)"
            }
            if(this.response.types[0].type.name =="psychic"){
                conten2.style.backgroundColor="	rgb(248,112,160)"
            }
            if(this.response.types[0].type.name =="fighting"){
                conten2.style.backgroundColor="	rgb(160,80,56)"
            }
            if(this.response.types[0].type.name =="ground"){
                conten2.style.backgroundColor="	rgb(234,214,164)"
            }
            if(this.response.types[0].type.name =="fairy"){
                conten2.style.backgroundColor="	rgb(231,159,231)"
            }
            if(this.response.types[0].type.name =="ghost"){
                conten2.style.backgroundColor="		rgb(96,96,176)"
            }
            if(this.response.types[0].type.name =="ice"){
                conten2.style.backgroundColor="		rgb(88,200,224)"
            }
        },
        atras(){
          this.$router.go(-1)
        }
  }
}


</script>


<style>
.conten2{
  height: 100%;
  width: 100%;
  padding: 20px;
  transition-duration: 1s;
 animation-duration: 1s;
 animation-name:slider ;
}
@keyframes slider{
  from{opacity: 0; 
    transform: translateX(45px)
  }
  to{
    transform: translateX(0);
        opacity: 1;
  }
}
.titulo{
  height: 20%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;
  color: white;
  font-weight: 800;

}
.info{
  display: flex;
  margin-top: 20px;
}
.info__imagen{
  width: 30%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.info__poke{
 height: 100%;
 width: 90%;

}

.info__texto{

  width: 100%;
  height: 50%;
  display: flex;
  justify-content: center;
  border-radius: 10px;
  perspective: 700px;

}
.stats{
  width: 30%;
  display: flex;
  flex-direction: column;
  align-items: center;

}
.abilities{
  width: 30%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.stats__title{
  font-size: 80px;
  color: white;
  font-weight: 700;
  
}
.line{
  height: 20px;
  width: 50px;
  border: solid 1px;
}
.stats__text{
  font-size: 30px;
  color: white;
  font-size: 30px;
  display: flex;
  justify-content: space-between;
  gap: 8rem;

}
.pictures{
  height: 50%;
  margin-top: 25px;

}
.pictures__title{
  height: 20%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;


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
.pictures__imagen{
  height: 100%;
  width: 100%;
}
.devolver__flecha{
  position: fixed;
  top: 300px;
  cursor: pointer;

}
.devolver__flecha:hover{
    transform: translateX(-20px);
}
</style>