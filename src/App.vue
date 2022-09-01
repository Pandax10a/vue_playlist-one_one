<template>
  <div id="app">
    <h1>Choose a song:</h1>
    <section v-for="(song, index) in songlists" :key="index">
      <article @click="selected_song(index)">
        
        <h3>Title: {{song.title}}</h3>
        
      </article>
    </section>
<div v-if="isEmpty">
  <p> pick a song </p>
        
</div>
<div v-else>
  <h1>currently playing: </h1>
  <!-- needed index so the variable updates dynamically and make it work after 1st click -->
  <article  :key="index">
  
   <p>{{current_song.title}}</p>
   <p>{{current_song.artist}}</p>
  
  <img :src="current_song.image_url">
  </article>
</div>
  </div>
  
  
</template>

<script>


export default {
//  set a truthy for testing if one of the object is empty
  methods: {
    selected_song(i) {
      
       
      this.current_song = this.songlists[i];
      if (this.current_song.artist === undefined) {
        this.isEmpty = true
      } else if(this.current_song.artist) {
        this.isEmpty = false
      }
      
      
      
      
    
     
    }
  },
  data() {
            return {
                songlists: [{
                    title: 'Bar Bar Bar',
                    artist: 'Crayon Pop',
                    song_id: 5576117192,
                    image_url: 'https://kpopping.com/documents/7c/5/Crayon-Pop-Bar-Bar-Bar-Concept-Teasers-3-Versions-documents-25.jpeg?v=b8fd6'
                },
                {
                    title: "I Can't Stop Me ",
                    artist: 'TWICE',
                    song_id: 5882688897,
                    image_url: 'http://images6.fanpop.com/image/photos/43600000/I-Can-t-Stop-Me-twice-jyp-ent-43612482-1500-1000.jpg'
                },
                {
                    title: 'Lion Heart',
                    artist: 'SNSD',
                    song_id: 4186615445,
                    image_url: 'https://seoulbeats.com/wp-content/uploads/2015/08/20150825_seoulbeats_snsd_girlsgeneration5-e1440413361127.jpg'
                },
                {
                    title: "As If It's Your Last",
                    artist: 'BLACKPINK',
                    song_id: 2235591632,
                    image_url: 'https://c-fa.cdn.smule.com/rs-s77/arr/5b/9d/cc4bed5a-55e9-46d6-965f-dcec4506b7ae_1024.jpg'
                },
                {
                    title: 'Never Gonna Give You Up',
                    artist: 'Rick Astley',
                    song_id: 6061798175,
                    image_url: 'https://i.ytimg.com/vi/dQw4w9WgXcQ/maxresdefault.jpg'
                }],
                current_song: {
                  title: "",
                  artist: "",
                  song_id: "",
                  image_url: "",
            },
            // truthy for checking if empty
            isEmpty: true
            }
        },
  name: 'App',
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
