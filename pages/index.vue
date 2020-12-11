<template>
  <div>

      <div class="container-fluid contentPage">
          <div class="row lignePrincipale">
              <div class="col-sm-2 navSoundcloud" id="sticky-sidebar">
                <p class="logoSoundcloud">SOUNCLOUD</p>

                    <!--Menu musique-->


                  <ul class="list-group list-group-flush grpListSoundcloud">
                      <li class="list-group-item lstSoundcloud">Favoris</li>
                      <li class="list-group-item lstSoundcloud">A l'écoute</li>
                      <li class="list-group-item lstSoundcloud"  @click="affichageFunk()">Rock</li>
                      <li class="list-group-item lstSoundcloud"  @click="affichageRock()">Pop</li>
                      <li class="list-group-item lstSoundcloud"  @click="affichageBlues()">Punk</li>
                  </ul>
              </div>
              <div class="col-sm-10 contentSoundcloud">
                    <h1 class="title">
                      À l'affiche                 
                    </h1>

                    <!--composant musique-->

                    <div class="composantMusique">
                      <musique v-if="affiche<1" @click.native="play(musiqueIndex)" v-for="(Musique, musiqueIndex) in Musiques" :son="Musique" :key="musiqueIndex"/>
                      <musique v-if="affiche==1&&Musique.Genre=='Funk'" @click.native="play(musiqueIndex)" v-for="(Musique, musiqueIndex) in Musiques" :son="Musique" :key="musiqueIndex"/>
                      <musique v-if="affiche==2&&Musique.Genre=='Rock'" @click.native="play(musiqueIndex)" v-for="(Musique, musiqueIndex) in Musiques" :son="Musique" :key="musiqueIndex"/>
                      <musique v-if="affiche==3&&Musique.Genre=='Blues'" @click.native="play(musiqueIndex)" v-for="(Musique, musiqueIndex) in Musiques" :son="Musique" :key="musiqueIndex"/>
                    </div>
              </div>
          </div>
          <div class="row lignePrincipale">

                    <!--Image Artiste en écoute-->

              <div class="col-sm-2 imgAritste" :style="imgAritste" id="sticky-sidebar">
                  <div style="height:350px;">
              </div>
              <div class="col-sm-10 contentVide">
                  <i class="fa fa-headphones"></i> {{artisteSelectionne}}
              </div>
          </div>
      </div>

                   <!--composant lecteur audio-->

      <div class=" sticki">
              <wavesurfer ref="wsf" :src="Musiques" :options="options"></wavesurfer>
      </div>
    </div>
  </div>
</template>

<script>
import musique from '~/components/musique.vue'

export default {
    data(){
      return{
        options: {
             progressColor: '#ffda43',
             waveColor: '#f7f7f7',
             responsive: true,
             barHeight: 0.4,
             cursorColor:'transparent',
             backgroundColor:'#2e2e2e', 
         },
        Musiques:[
          /* Rock */
          {
            Titre: 'Waiting For Nothing',
            Images: '/music_photo/Rock/The_Fisherman.jpeg',
            Description: ' ',
            Src: '/Musique/Rock/1_TheFisherman_Waiting_For_Nothing.mp3',
            Artiste: 'The Fisherman ',
            Genre: 'Rock',


          },
          {
            Titre: 'Night',
            Images: '/music_photo/Rock/Cloudkicker.jpeg',
            Description: ' ',
            Src: '/Musique/Rock/2_Cloudkicker_Night.mp3',
            Artiste: 'Cloudkicker ',
            Genre: 'Rock',
          },
          {
            Titre: 'My Little Kingdom',
            Images: '/music_photo/Rock/Golden_Duck_Orchestra.jpeg',
            Description: ' ',
            Src: '/Musique/Rock/3_Golden_Duck_Orchestra_-_My_Little_Kingdom.mp3',
            Artiste: 'Golden Duck O ',
            Genre: 'Rock',


          },
          {
            Titre: 'No love',
            Images: '/music_photo/Rock/Shearer.jpeg',
            Description: ' ',
            Src: '/Musique/Rock/4_Shearer-NoLove.mp3',
            Artiste: 'Shearer ',
            Genre: 'Rock',
          },
          {
            Titre: ' Days past',
            Images: '/music_photo/Rock/In_Closing.jpeg',
            Description: ' ',
            Src: '/Musique/Rock/5_Days-past.mp3',
            Artiste: 'In closing ',
            Genre: 'Rock',
          },

    /* Funk */

          {
            Titre: 'Crazy',
            Images: '/music_photo/Funk/Anozira.jpeg',
            Description: ' ',
            Src: ' /Musique/Funk/1_Anozira-Crazy.mp3',
            Artiste: 'Anozira ',
            Genre: 'Funk',


          },
          {
            Titre: 'Daily Dozen',
            Images: '/music_photo/Funk/Astat.jpeg',
            Description: ' ',
            Src: '/Musique/Funk/2_Astat_-_Daily_Dozen.mp3',
            Artiste: 'Astat ',
            Genre: 'Funk',


          },
          {
            Titre: 'Translate ',
            Images: '/music_photo/Funk/Artner.jpeg',
            Description: ' ',
            Src: '/Musique/Funk/3_Translate.mp3',
            Artiste: 'Artner',
            Genre: 'Funk',


          },
          {
            Titre: 'Muse De Funk ',
            Images: '/music_photo/Funk/Ruby_Cassaya.jpeg',
            Description: ' ',
            Src: '/Musique/Funk/4MuseDeFunk.mp3',
            Artiste: 'Ruby Cassaya',
            Genre: 'Funk',
          },
          {
            Titre: 'Opening para',
            Images: '/music_photo/Funk/Songo_21.jpeg',
            Description: ' ',
            Src: '/Musique/Funk/5_Opening para_Songo 21.mp3',
            Artiste: 'Songo 21',
            Genre: 'Funk',


          },
/* Blues */
          {
            Titre: 'Will You Whisper ',
            Images: '/music_photo/Blue/Pierce_Murphy.jpeg',
            Description: ' ',
            Src: '/Musique/Blue/PierceMurphy-WillYouWhisper.mp3',
            Artiste: 'Pierce Murphy',
            Genre: 'Blues',


          },

          {
            Titre: 'Home Sweet Home',
            Images: '/music_photo/Blue/Stuart_Evans.jpeg',
            Description: ' ',
            Src: '/Musique/Blue/2_StuartEvansMusic_HomeSweetHome.mp3',
            Artiste: 'Stuart Evans',
            Genre: 'Blues',


          },


          {
            Titre: 'A Foolish Game ',
            Images: '/music_photo/Blue/Madam_Snowflake.jpeg',
            Description: ' ',
            Src: '/Musique/Blue/3_snowflake_-_A_Foolish_Game.mp3',
            Artiste: 'Madam Snowflake',
            Genre: 'Blues',


          },

          {
            Titre: 'The River’s Going Wild  ',
            Images: '/music_photo/Blue/Black_Island_Hood.jpeg',
            Description: ' ',
            Src: '/Musique/Blue/4_1TheRiversGoingWild.mp3',
            Artiste: 'Black Island Hood    ',
            Genre: 'Blues',


          },

          {
            Titre: 'Sofa  ',
            Images: '/music_photo/Blue/Dazie_Mae.jpeg',
            Src: '/Musique/Blue/5_Sofa_Dazie Mae.mp3' ,
            Artiste: 'Dazie Mae ',
            Genre: 'Blues',


          }
        ],
        affiche:'',
        imgAritste :{
            backgroundImage: "url('/music_photo/Rock/The_Fisherman.jpeg')",
            backgroundSize: "cover",
        }, 
        artisteSelectionne:''
      }
  },
  components :{
    musique
  },
  methods :{
        //Pour lancer la musique quand on clique dessus

        play(position){
          this.$refs.wsf.play(this.Musiques[position].Src);
          this.imgAritste.backgroundImage="url("+this.Musiques[position].Images+")";
          this.artisteSelectionne=this.Musiques[position].Titre;
        }, 

        //Pour afficher les musiques par genre

        affichageFunk(){
          this.affiche= 1;
        },        
        affichageRock(){
          this.affiche= 2;
        },        
        affichageBlues(){
          this.affiche= 3;
        },
  }
}
</script>

<style>
html, body {
  height: 100%;
  display: flex;
  flex-direction: column;
  background-color:black;
}


.logoSoundcloud{
  color:#ffda43;
  font-size:50px;
  font-weight:bold;
  background-color:black;
  background-size: 10px 10px; 
  margin-top:20px;
  margin-bottom:50px;
}
.navSoundcloud{
  background-color:#2e2e2e;
}

.lstSoundcloud{
  background-color:#2e2e2e;
  color:#ffda43;
  font-size:25px;
  font-weight:bold;
  margin-top:20px;
  margin-bottom:20px;
}
.grpListSoundcloud{
  margin-bottom:50px;
}
.contentSoundcloud{
  background-color:black;
  color:#ffda43;
}
.contentVide {
  color:#ffda43;
  font-size:30px;
}
.sticki{
  flex-shrink: 0;
}
.lignePrincipale{
  flex: 1 0 auto;
  width:100%;
}

h1{
  font-weight:bold;
  margin:20px;
  font-size:90px;
}


button{
  color:white;
}
.composantMusique{
    display: flex;
    flex-wrap: wrap;
}
</style>
