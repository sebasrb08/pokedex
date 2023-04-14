<template>
        <NuxtLink :to="nombre">   
            <div class="card__contenedor">
                <div class="card__id">
                    <span>#{{ id }}</span>
                </div>
                <div class="card__img">
                    <img :src="url" alt="">
                </div>
                <div class="card__text">
                    <h4>{{ nombre }}</h4>
                </div>
                </div>
        </NuxtLink>
</template>

<script>
export default {
    name:'CardPage',
    props:{
        nombre:{
            type:String,
            required:true
        },
        url:{
            type:String,
            required:true
        },
        id:{
            type:Number,
            required:true
        }
    }
  
}

</script>


<style>

.card__contenedor{
    height: 100%;
    width: 100%;
    background: rgb(255,255,255);
background: linear-gradient(0deg, rgba(255,255,255,1) 17%, rgba(245,51,48,1) 87%);
    font-size: 30px;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    
    border-radius: 10px;
    box-shadow: 0px 10px 10px rgb(0, 0, 0);
    border: solid 5px MidnightBlue	;

}

h4{
    font-size: 40px;
    font-weight: 500;
}
.card__id{
width: 100%;
height: 10%;
color: black;
opacity: 0.5;
}
.card__img{
    height: 70%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
.card__text{
    height: 20%;
    display: flex;
    align-items: center;
    color: black;
}
img{
    height: 200px;
    width: 100px;
}

</style>