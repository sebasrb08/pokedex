<template>
    <div>
        <p>{{ nombre }}</p>
        <img v-if="mostrar" src="https://thumbs.dreamstime.com/b/sentada-del-perrito-de-labrador-30817211.jpg" alt="">
        <button @click="cambiar">cambiar Nombre</button>
    </div>
</template>

<script>
export default{
    name:'PruebaPage',
    data(){
        return{
            nombre:'Sebastian',
            mostrar:true
        }
    },
    methods:{
        cambiar(){
            if(this.nombre =='Sebastian'){
            this.nombre = 'Rueda Bedoya'
            this.mostrar=false
            }else{
                this.nombre='Sebastian'
                this.mostrar=true
            }
        }
    }
}
</script>

<style>
button{
    background-color: blue;
}
img{
    height: 100px;
    width: 100px;
}
</style>