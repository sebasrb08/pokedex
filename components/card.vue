<template>
        <NuxtLink :to="nombre">   
            <div class="card__contenedor">
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
        }
    }
  
}

</script>


<style>

.card__contenedor{
    height: 100%;
    width: 100%;
    background-color: rgba(245, 116, 30, 0.836);
    font-size: 30px;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    
    border-radius: 10px;
    box-shadow: 0px 10px 10px rgb(0, 0, 0);
    border: solid 5px white;
    animation-name:cardss ;
    animation-duration: 1s;
    animation-iteration-count: infinite;

}
@keyframes cardss{
    0%   {background-color: rgba(245, 116, 30, 0.836); left:0px; top:0px;}
  50%  {background-color:blue; left:200px; top:200px;}
  100% {background-color: rgba(245, 116, 30, 0.836); left:0px; top:0px;}
}
h4{
    font-size: 40px;
    font-weight: 500;
}
.card__img{
    height: 80%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
.card__text{
    height: 20%;
    display: flex;
    align-items: center;
}
img{
    height: 60%;
    width: 60%;
}

</style>