<template>
<div>
<h1 class='kanye-title'>Kanye West at his Kanye Best</h1>
 <h2>{{ quote }}</h2>
<img class='kanye-image' src='https://specials-images.forbesimg.com/imageserve/5f95799528c4c5529897c81b/960x0.jpg?fit=scale'>
<button class='button' v-on:click='newKanyeQuote'>KANYE SPEAK</button>

</div>
</template>
<script>
export default {
    name: 'kanye-quote',
    props: ['quote'],
    methods: {
        newKanyeQuote() {
            fetch('https://api.kanye.rest/')
            .then(res => res.json())
            .then(KanyeQuote => this.quote = KanyeQuote.quote)
        }
    }

}
</script>
<style lang='css' scoped>
.kanye-title {
    padding: 15px;
    background-color: rgb(3, 3, 3);
    color: rgb(252, 228, 248);
    font-family: 'Rock Salt', cursive;
    
}
.button {
   display: flex; 
   padding: 20px; 
   border-radius: 6px;
   font-family: 'Rock Salt', cursive;
   background-color: rgb(0, 0, 0); 
   color: rgb(252, 228, 248);
}
.kanye-image {
   padding: 20px; 
   width: 400px; 
   height: auto;
}
</style>
















