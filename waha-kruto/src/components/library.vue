<template lang="pug">

.wrapper
    header.header
        .container
        .headline
          h1.header__name(@click="resetFilter") Ваха круто
          .open-navigation.button(@click="switchNavigation")
            .open-navigation__triangle.open-navigation__triangle--down(v-if="!openNavigation")
            .open-navigation__triangle.open-navigation__triangle--up(v-if="openNavigation")

         
        p.header__description Золотой пантеон книг по вархаммеру 
        nav.navigation
          
          ul.navigaton-list(:class="{ navigationListOpened: openNavigation }")
            li.navigaton-list__item(@click="resetFilter" :class="{ active: noFilterApplied }") Все книги
             
                
            li.navigaton-list__item(@click="filterHeresy" :class="{ active: isHeresySelected }") Ересь Хоруса
            li.navigaton-list__item(@click = "filter40k" :class="{ active: is40kSelected }") 40К 
            

    main.maincontent
        .container
          
            
        
            ul.books-list
                li.books-list__item(v-for = "book in books" )
                    book(:book="book" )
    footer.footer 
       .container 
        .disclaimer Где я и что происходит

    
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
    openNavigation: false,
    noFilterApplied: true

    }
 
    },
    created(){
        let data = require('../jsons/library.json'); this.books = data
    },
    methods: {
   
        resetFilter(){
            let data = require('../jsons/library.json'); this.books = data;
           
     
            this.isHeresySelected = false;
            this.is40kSelected = false;
            this.noFilterApplied = true
            
        },
        filterHeresy(){
            let data = require('../jsons/library.json'); this.books = data;
            this.books = this.books.filter(books => books.setting === "Ересь Хоруса");
            this.setting = "Ересь Хоруса";
            this.isHeresySelected = true;
            this.is40kSelected = false;
            this.noFilterApplied = false;
           },
        
        filter40k(){let data = require('../jsons/library.json'); this.books = data;
            this.books = this.books.filter(books => books.setting === "40K");
            this.setting = "40K";
            this.isHeresySelected = false;
            this.is40kSelected = true;
            this.noFilterApplied = false;
            },
        switchNavigation(){this.openNavigation=!this.openNavigation}

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
  margin: 0 auto;
  position: relative
}

.header {
  flex: 0 0 auto;
 font-family: 'Spectral SC', serif;
 font-weight: bold;
 font-size: 56rem;
 text-align: center;
 color: #fff;
 background-color: #030706;
 
}

.header__name {line-height: 1em; cursor: pointer}

.header__description {
  font-size: 16rem;
  color: #d8a941;
  @media (max-width: 560px) {display: none}
}

.maincontent {
  flex: 1 0 auto;
  display: flex;
  flex-direction: column;
  
  font-family: 'Spectral SC', serif;
  background: #fffafa
 
}

.footer {
    flex: 0 0 auto;
 font-family: 'Spectral SC', serif;
 font-weight: bold;
 font-size: 24rem;
 text-align: center;
 color: #fff;
 background-color: #030706;
}

.navigaton-list {display: flex; font-size: 14rem; width: 100%; justify-content: center; transition: 0.3s;
@media (max-width: 560px) {
  flex-direction: column;
  height: 0;
  overflow: hidden;
  font-size: 20rem
}}

.navigaton-list__item {padding:0 20rem; border-left: 2px solid #fff;
&:hover{color:#d8a941;
border-left:2px solid #d8a941}
&:first-child{border-left: none;
padding-left: 0};
cursor: pointer;
@media (max-width: 560px){padding: 0; border-left: none;
&:hover {border-left: none}}

}

.navigation-list__picture-box {height: 20rem; display: flex; justify-content: center;}
.books-list{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    justify-items: center;
    grid-gap: 15rem;
    margin-top: 25rem;
    @media (max-width: 768px) {grid-template-columns: 1fr 1fr
      
    };
    @media (max-width: 569px) {grid-template-columns: 1fr}
    
}

.active {
color:#d8a941;
border-left:2px solid #d8a941;
&:first-child{border-left: none};


@media (max-width: 560px) {border-left: none };
}

.books-list__item {height: 500rem; width: 100%}

.open-navigation { 
display: none;


@media (max-width: 560px) {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 10rem;
}}

.navigationListOpened {height: 130rem;
transition: 0.3s}



.open-navigation__triangle--up {
width: 0; 
height: 0;
border-left: 15rem solid transparent;
border-right: 15rem solid transparent;
border-bottom: 30rem solid #d8a941;
cursor: pointer;

}

.open-navigation__triangle--down {width: 0; 
height: 0;
border-left: 15rem solid transparent;
border-right: 15rem solid transparent;
border-top: 30rem solid #d8a941;
cursor: pointer;}

.headline {display: flex;
justify-content: center;
@media (max-width: 560px) {justify-content: space-between}}
</style>