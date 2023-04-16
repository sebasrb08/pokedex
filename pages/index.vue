<template>
    <loading v-if="loading" />

    <div  class="contenedorF" v-else>
        <div class="boton__left">
                    <button v-if="atras2" @click="atras"><img class="card__boton--atras" src="/atras.svg" alt=""></button>
                </div>
        <div class="contenedor" >
            <div class="titulo2">
                <h1>Pokedex</h1>
            </div>
            <div class="buscador">
                <form @submit.prevent="busqueda">
                    <input v-model="search" type="text" class="buscar" placeholder="Buscar Pokemon">
                </form>
            </div>
            <div class="card__conten">
                <div v-for="i in response" :key="i.name" class="card"  >
                    <card  :id="i.id" :nombre="i.name" :url="i.sprites.other.dream_world.front_default" />
                </div>
            </div>
    
        </div>
        <div class="boton__right">
            <button v-if="next" @click="getInfo2"><img class="card__boton--siguiente" src="/next.svg" alt=""></button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PokeapiPage',
    data() {
        return {
            response: [],
            search: "",
            loading: true,
            cont:1,
            atras2:false,
            next:true,
            fire:false,
            all:"hola"
        }
    },
    mounted() {
        this.getInfo()
        
    },
    methods: {
        async getInfo() {
            try {

                if(this.cont ===  1){
                    this.atras2=false
                    this.response=[]
                    for (let j = 1; j <= 20; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    
                    }

                    
                }else if(this.cont === 2){
                    this.atras2=true
                    this.response=[]
                    for (let j = 21; j <= 40; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    }
                }else if(this.cont === 3){
                    this.response=[]
                    for (let j = 41; j <= 60; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    }
                }else if(this.cont === 4){
                    this.response=[]
                    for (let j = 61; j <= 80; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    }
                }else if(this.cont === 5){
                    this.response=[]
                    for (let j = 81; j <= 100; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    }
                }else if(this.cont === 6){
                    this.response=[]
                    for (let j = 101; j <= 120; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    }
                }else if(this.cont === 7){
                    this.next=true
                    this.response=[]
                    for (let j = 121; j <= 140; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false

                    }
                }
            else if(this.cont === 8){
                    this.next=false
                    this.response=[]
                    for (let j = 141; j <= 151; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false

                    }
                }
                        

            } catch (e) {

            }
        },
        getInfo2() {
            this.cont++
            this.getInfo()
        
        },
        atras(){
            this.cont--
            this.getInfo()

        },
      
        busqueda() {
            this.response.forEach(elements => {
                if(elements.name==this.search){
                this.$router.push(`/${this.search}`)
            }

            });

        }
    },
}


</script>

<style>
.contenedorF{
    height: 100%;
    width: 100%;
    display: flex;
    background-color:#1a1831	;

}
.contenedor {
    height: 100%;
    width: 90%;
    padding: 20px;
}
.titulo2 {
    height: 10%;
    width: 100%;
    background: red;
    display: flex;
    justify-content: center;
    align-items: center;
    color: yellow;
    text-shadow: -3px -3px 3px #0000DF, 3px -3px 3px #0000DF, -3px 3px 3px #0000DF, 3px 3px 3px #0000DF;
    font-size: 65px;
    font-weight: 800;
    border-radius: 10px;

}
.buscador {
    height: 15%;
    width: 100%;
    margin-top: 20px;

}
.buscar{
    width: 30%;
    border-radius: 50px;
    font-size: 20px;
    padding: 10px;
}

.card__conten {
    height: 70%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-top: 10px;
    transition-duration: 3s;
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
.card {
    width: 23%;
    transition-duration: 1s;
    animation-duration: 2s;
    animation-name:slider ;

    
}

.boton__left{
    height: 100%;
    width: 5%;
    display: flex;
    align-items: center;
}
.boton__right{
    height: 100%;
    width: 5%;
    display: flex;
    align-items: center;
}
.card__boton--atras{
    left: 0;
    top: 250px;
    position: fixed;
    opacity: 0.5;

}
.card__boton--atras:hover{
    transform: translateX(-20px);

}
.card__boton--siguiente{
    position: fixed;
    right: 0;
    top: 250px;
    opacity: 0.5;
    cursor: pointer;
}
.card__boton--siguiente:hover{
    transform: translateX(20px);

}
</style>