<template lang="pug">

.wrapper
    header.header
        .container
         h1.header__name Ваха круто
         p.header__description Золотой пантеон книг по вархаммеру 
         nav.navigation
          ul.navigaton-list
            li.navigaton-list__item 
              .navigation-list__picture-box(@click="resetFilter")
                img(src="../assets/aquilla.png")
            li.navigaton-list__item(@click="filterHeresy" :class="{ active: isHeresySelected }") Ересь Хоруса
            li.navigaton-list__item(@click = "filter40k" :class="{ active: is40kSelected }") 40К 
            li.navigaton-list__item Где я и что происходит

    main.maincontent
        .container
          .library
            
        
            ul.books-list
                li.books-list__item(v-for = "book in books" :isFiltered="isFiltered")
                    book(:book="book" :isFiltered="isFiltered")
    footer.footer 
       .container очень круто

    
</template>

<script>
import book from "../components/book"

export default {
    components: {book},
    data(){return{
    books:[],
    setting:'',
   
    isHeresySelected: false,
    is40kSelected: false,
    }
 
    },
    created(){
        let data = require('../jsons/library.json'); this.books = data
    },
    methods: {
   
        resetFilter(){
            let data = require('../jsons/library.json'); this.books = data;
           
     
            this.isHeresySelected = false;
            this.is40kSelected = false
            
        },
        filterHeresy(){
            let data = require('../jsons/library.json'); this.books = data;
            this.books = this.books.filter(books => books.setting === "Ересь Хоруса");
            this.setting = "Ересь Хоруса";
            this.isHeresySelected = true;
            this.is40kSelected = false
           },
        
        filter40k(){let data = require('../jsons/library.json'); this.books = data;
            this.books = this.books.filter(books => books.setting === "40K");
            this.setting = "40K";
            this.isHeresySelected = false;
            this.is40kSelected = true
            }

    },
    

}
</script>

<style lang="scss">
.wrapper {
  width: 100%;
  margin: 0 auto;
  height: 100vh;
  display: flex;
  flex-direction: column;
  
}

.container {
  width: 90%;
  margin: 0 auto
}

.header {
  flex: 0 0 auto;
 font-family: 'Spectral SC', serif;
 font-weight: bold;
 font-size: 56rem;
 text-align: center;
 color: #fff;
 background-color: #000;
 
}

.header__name {line-height: 1em}

.header__description {
  font-size: 16rem;
  color: #d8a941
}

.maincontent {
  flex: 1 0 auto;
  display: flex;
  flex-direction: column;
  
  font-family: 'Spectral SC', serif;
 
}

.footer {
    flex: 0 0 auto;
 font-family: 'Spectral SC', serif;
 font-weight: bold;
 font-size: 24rem;
 text-align: center;
 color: #fff;
 background-color: #000;
}

.navigaton-list {display: flex; font-size: 14rem; width: 100%; justify-content: center;}

.navigaton-list__item {padding:0 20rem; border-left: 2px solid #fff;
&:hover{color:#d8a941;
border-left:2px solid #d8a941}
&:first-child{border-left: none;
padding-left: 0};
cursor: pointer;

}

.navigation-list__picture-box {height: 20rem;}
.books-list{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    justify-items: center;
    grid-gap: 15rem;
    margin-top: 25rem;
    
}

.active {color:#d8a941;
border-left:2px solid #d8a941}

.books-list__item {height: 500rem; width: 100%}
</style>