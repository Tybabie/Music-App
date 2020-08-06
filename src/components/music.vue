<template>
  <div id="landing" >
  <header>
    <h2 id="title">{{current.title}} - {{current.artist}} </h2>
      <div class="controls">
        <button class="prev" @click="prev">Prev</button>
        <button class="play" v-if="!isPlaying" @click="play" >Play</button>
        <button class="pause" v-else @click="pause">Pause</button>
        <button class="next" @click="next">Next</button>
      </div>
  </header>
  <main>
    <section class="playlist">
      <h3>All Songs</h3>
      <div v-for="song in songs" :key="song.src" @click="play(song)" 
      v-bind:class="(song.src == current.src) ? 'song playing' : 'song' ">
         <b> {{song.title}} </b> <br> <i> {{song.artist}}</i> <br><br>
      </div>
    </section>
  </main>
  </div>
</template>

<script>
export default {
  name: 'music',
  data(){
    return{
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {title: 'Promise', 
        artist: 'Adekunle_Gold nd Simi',
        src : require('../assets/music/Adekunle-Gold-x-Simi-Promise.mp3')
        },
        {
        title: 'Something-Different', 
        artist: 'Adekunle_Gold',
        src : require('../assets/music/Adekunle-Gold-Something-Different.mp3')
        },
        {
        title: 'Risky', 
        artist: 'Davido-Ft.-Popcaan',
        src : require('../assets/music/Davido-Ft.-Popcaan-Risky.mp3')
        },
        {
        title: 'Tiff', 
        artist: 'Demmie-Vee',
        src : require('../assets/music/Demmie-Vee-–-Tiff.mp3')
        },
        {
        title: 'Up-To-Something', 
        artist: 'Mayorkun',
        src : require('../assets/music/Mayorkun-Up-To-Something.mp3')
        },
        {
        title: 'Bad-Boys', 
        artist: 'Rema-Beamer-ft.-Rvssian',
        src : require('../assets/music/Rema-Beamer-Bad-Boys-ft.-Rvssian.mp3')
        },
        {
        title: 'Duduket', 
        artist: 'Simi',
        src : require('../assets/music/Simi-Duduke.mp3')
        },
        {
        title: 'Selense', 
        artist: 'Simi',
        src : require('../assets/music/Simi-–-Selense.mp3')
        },
        {
        title: 'Jericho', 
        artist: 'Simi-Ft.-Patoranking',
        src : require('../assets/music/Simi-Ft.-Patoranking-Jericho.mp3')
        },
        {
        title: 'Mind-Your-Bizness', 
        artist: 'Simi-Ft.-Falz',
        src : require('../assets/music/Simi-Ft.-Falz-–-Mind-Your-Bizness.mp3')
        },
        {
        title: 'Blow', 
        artist: 'Wizkid',
        src : require('../assets/music/Wizkid-Blow-Prod.-by-Blaqjerzee.mp3')
        },
        {
        title: 'Owo-Mi-Da', 
        artist: 'Tiwa-Savage',
        src : require('../assets/music/Tiwa-Savage-–-Owo-Mi-Da.mp3')
        },
        {
        title: 'Billionaire', 
        artist: 'Teni',
        src : require('../assets/music/Teni-Billionaire.mp3')
        },
        {
        title: 'Fall-In-Love', 
        artist: 'T-Classic-Ft-Mayorkun',
        src : require('../assets/music/T-Classic-Ft-Mayorkun-Fall-In-Love-Prod-By-Killertunes-1.mp3')
        },
        {
        title: 'You-Mean-To-Tell-Me', 
        artist: 'Tatiana-Manaois',
        src : require('../assets/music/Tatiana-Manaois-You-Mean-To-Tell-Me.mp3')
        },
        {
        title: 'I Need Your Love ', 
        artist: 'Calvin Harris feat. Ellie Goulding',
        src : require('../assets/music/Calvin Harris feat. Ellie Goulding - I Need Your Love (parole).mp3')
        },
        {
        title: 'Pawon', 
        artist: 'Olamide',
        src : require('../assets/music/Olamide_Pawon.mp3')
        },
        {
        title: 'Beauty Sings', 
        artist: 'Tatiana Manaois',
        src : require('../assets/music/Beauty Sings - Tatiana Manaois (Mp3Goo.io).mp3')
        },
        {
        title: 'Scatter', 
        artist: 'Fireboy',
        src : require('../assets/music/Fireboy-DML-Scatter.mp3')
        }
      ],
      player: new Audio()
    }
  },
  created(){
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  methods: {
    play(song){
      if(typeof song.src != 'undefined'){
        this.current =  song;
        this.player.src = this.current.src;
         
      }
      this.player.play(this.current);
      this.isPlaying = true;
      document.getElementById('landing').style.background = 
      "linear-gradient(rgba(0, 0, 255, 0.9)1%, rgba(0, 0, 0, 0.9)),url(https://i.pinimg.com/originals/05/4a/a3/054aa3421c22e0c9e04ada3082066a8d.gif)"
      document.getElementById('landing').style.backgroundRepeat = 'no-repeat';
      document.getElementById('landing').style.backgroundSize = 'cover';
      document.getElementById('landing').style.backgroundPosition = 'center';
       document.getElementById('landing').style.backgroundAttachment = 'fixed'
    },
    pause(){
      this.player.pause();
      this.isPlaying = false;
      document.getElementById('landing').style.background = 
      'linear-gradient(rgb(0, 0, 0, 0.8), rgba(0, 0, 0, 0.9)),  url(http://www.desktopwallpaperhd.net/wallpapers/22/e/music-themes-background-228094.jpg)'
      document.getElementById('landing').style.backgroundRepeat = 'no-repeat';
      document.getElementById('landing').style.backgroundSize = 'cover';
      document.getElementById('landing').style.backgroundPosition = 'center';
       document.getElementById('landing').style.backgroundAttachment = 'fixed'
    },
    next(){
      this.index++;
      if (this.index > this.songs.length -1) {
        this.index = 0;
       
      }
       this.current = this.songs[this.index];
        this.play(this.current);
    },
    prev(){
      this.index--;
      if (this.index < 0 ) {
        this.index = this.songs.length -1;
      }
      this.current = this.songs[this.index];
        this.play(this.current);
    },

  }
  }

</script>


<style>
*{
 box-sizing: border-box;
 margin: 0px;
  padding: 0px;
}
body{
  margin: 0px;
  padding: 0px;
}
#landing{
background: linear-gradient(rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.9)), url('../assets/images/bg.jpg');
background-repeat: no-repeat;
background-size: cover;
background-position: center;
background-attachment: fixed;
color: white;
height: auto;
}
header{
text-align: center;
 background-color: rgba(0, 0, 0, 0.596);
  color: white;
  padding: 10px;
  position: fixed;
  width: 100%;
}
.playlist{
  padding-top: 20vh;
  padding-left: 10px;
  padding-bottom: 10vh;
}
.playlist h3{
  font-size: 40px;
  margin-bottom: 25px;
}
.playlist div{
  font-size: 20px;
}
button{
  padding: 5px 10px;
  margin: 20px 15px 0px 15px ;
  outline: none;
  background-color: black;
  color: blanchedalmond;
}
@media only screen and  (max-width: 760px) {
  .playlist{
  padding-top: 30vh;
}
}
</style>
