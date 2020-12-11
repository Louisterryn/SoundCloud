<template>
    <div>
        <div class="center-block bloc">
            <div class="surbrillance">
                <img class="imgMusique" :src="son.Images"/>
                <p class="artisteMusique"><i class="fa fa-heart"></i> {{son.Artiste}}</p>
                <p class="titreMusique">{{son.Titre}}</p>
            </div>
        </div>
    </div>
</template>
<script>
 export default {
    name : "musique",
    props : ["son"],
  }
</script>
<style>
.bloc{
    margin:50px;
    margin-top:100px;
    border: solid 8px #ffda43;
    border-radius:20px;
    padding:20px;
}
.surbrillance:hover{
    background-color:white;
    opacity:0.7;
}
.imgMusique{
    width:300px;
    height:300px;
}
.titreMusique{
    font-size:20px;
}
.artisteMusique{

    font-size:30px;

}
</style>