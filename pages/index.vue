<template>
    <loading v-if="loading" />
    <div class="contenedor" v-else>
        <div class="titulo2">
            <h1>Pokedex</h1>
        </div>
        <div class="buscador">
            <form @submit.prevent="busqueda">
                <input v-model="search" type="text" class="buscar" placeholder="Buscar Pokemon">
            </form>
        </div>
        <div class="card__conten">
            <div v-for="i in response" :key="i.name" class="card">
                <card :id="i.id" :nombre="i.name" :url="i.sprites.other.dream_world.front_default" />
                

            </div>
        </div>
        <div class="card__boton">
            <div class="boton__left">
                <button v-if="atras2" @click="atras"><img class="card__boton--atras" src="/pikachu.png" alt=""></button>
            </div>
            <div class="boton__right">
                <button v-if="next" @click="getInfo2"><img class="card__boton--siguiente" src="/pikachu.png" alt=""></button>
            </div>
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
            fire:"red"
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
                    this.next=true
                    this.response=[]
                    for (let j = 101; j <= 120; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false
                    }
                }else if(this.cont === 7){
                    this.next=false
                    this.response=[]
                    for (let j = 121; j < 141; j++) {
                        const { data } = await this.$axios.get(`pokemon/${j}`)
                        this.response.push(data)
                        this.loading = false

                    }
                }
                

            } catch (e) {
                console.log(e)
            }
        },
        getInfo2() {
            this.cont++
            console.log(this.cont)
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
.contenedor {
    height: 100%;
    width: 100%;
    background-color:#1a1831	;
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

input {
    width: 20%;
    border: solid black 3px;
    font-size: 25px;
}

.card__conten {
    height: 70%;

    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 30px;
    margin-top: 10px;
}

.card {
    width: 23%;

}
.card__boton{
    height: 15%;
    width: 100%;
    margin-top: 25px;
    display: flex;
    gap: 20px;

}
.boton__left{
    height: 100%;
    width: 50%;
    display: flex;
    justify-content: end;
}
.boton__right{
    height: 100%;
    width: 50%;
    display: flex;
    justify-content: start;
}
.card__boton--atras{
    height: 100%;
    width: 100%;
    transform: rotate(270deg);    
}
.card__boton--siguiente{
    height: 100%;
    width: 100%;
    transform: rotate(90deg);    
}
</style>