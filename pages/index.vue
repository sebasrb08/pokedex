<template>
    <div class="contenedor">
        <div class="titulo">
            <h1>Pokedex</h1>
        </div>
        <div class="buscador">
            <input v-show="busq" type="text" class="buscar"  placeholder="Buscar Pokemon">
        </div>
        <div class="card__conten">
            <div v-for="i in response" :key="i.name" class="card">
                    <card :nombre="i.name" :url="i.sprites.other.dream_world.front_default"/>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name:'PokeapiPage',
    data(){
        return{
            response: [],
            busq:true,
        }
    },
    mounted(){
        this.getInfo()
    },
    methods:{
        async getInfo(){
            for(let j=1;j<150;j++){
                const {data} = await this.$axios.get(`pokemon/${j}`)
                this.response.push(data)
                
            }
        }
        }
}
    // methods:{
    //     vista(){
    //         location.href='./pokeapi2'
    //     }
    // },



</script>

<style>

.contenedor{
    height: 100%;
    width: 100%;
    background-color: lightcyan;
   padding: 20px;
}
.titulo{
    height: 10%;
    width: 100%;
    background-color: rgba(245, 116, 30, 0.836);
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 50px;
    font-weight: 800;
    border-radius: 10px;
    
}
.buscador{
    height: 15%;
    width: 100%;
    margin-top:20px ;

}
input{
    width: 20%;
    border: solid black 3px;
    font-size: 25px;
}
.card__conten{
    height: 70%;
    
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin-top: 10px;
}
.card{
    width: 23%;
   
}
</style>