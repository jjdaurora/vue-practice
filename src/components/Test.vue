<template>
        <div class="test-app">
        <h1 class="header">{{msg}}</h1>
        <input v-model="searchTerm" type="text"> 
        <button class="button" @click=getGifs()>
            Search
        </button><br/><br/>
        <div class="gif-container">
            <img v-for="gif in gifs" :src="gif" :key="gif.id"/><br/>
        </div>
    </div>
    
</template>

<script>


export default {
   name: "Test",
   props: {
       msg: String,
       searchTerm: "",
       gifs: []
   },
   methods: {
       getGifs() {
        const apiKey = "2v9dfl3zsS4cA3RwsbYIniZFedL1DTww";
        const searchEndPoint =  "https://api.giphy.com/v1/gifs/search?";

        let url = `https://api.giphy.com/v1/gifs/search?&api_key=2v9dfl3zsS4cA3RwsbYIniZFedL1DTww&q=${this.searchTerm}&limit=5"`

        fetch(url)
            .then(response => {
                return response.json();
            })
            .then(json => {
                this.buildGifs(json);
            })
            .catch(err=> {
                console.log(err);
            })
          
       },
           buildGifs(json){
            this.gifs = json.data
                .map(gif=> gif.id)
                .map(gifId => {
                    return `https://media.giphy.com/media/${gifId}/giphy.gif`;
                })

        }
   },
};
</script>

<style scoped>

img {
    max-width: 50%;
    max-height: 50%;
}
</style>
