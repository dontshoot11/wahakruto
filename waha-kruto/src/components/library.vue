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
            li.navigation-list__item
              input.settings.settings--desktop(type="range" min="1" max="3" v-model="gridSetting")
              .settings--mobile
                input.settings__radio(type="radio" value="1" name="mobileButton" v-model="gridSetting")
                input.settings__radio(type="radio" value="2" name="mobileButton" v-model="gridSetting")
           
            

    main.maincontent
        .container
          
            
        
            ul.books-list(:class="{ mediumGrid: currentGrid == 2, smallGrid: currentGrid == 1, hugeGrid: currentGrid == 3}" )
                li.books-list__item(v-for = "book in books" )
                    book(:book="book" )
    footer.footer 
       .container 
        .disclaimer Где я и что происходит
          .disclaimer-popup 
            .disclaimer-popup__logo
              img(src="https://i.imgur.com/H54pSDl.png").disclaimer-popup__picture
            .disclaimer-popup__description
              p.disclaimer-popup__text Вархаммер - удивительная фантастическая вселенная. Если рассматривать художественную литературу, то, по-сути, она производится как на конвейере, по четкому плану, сугубо для поддержания продаж настольных игр. Однако, так уж случилось, что над книгами работает команда очень талантливых авторов, которым раз за разом получается презвойти самих себя и издавать, без шуток, выдающиеся произведения.
              
              p.disclaimer-popup__text Я - просто ноунейм из интернета, без претензии на что-то вообще, решил собрать, скорее для себя, лучшие из лучших. 
              p.disclaimer-popup__text Эта страничка вряд ли будет часто обновляться, потому что здесь собраны действительно самые-самые произведения, 10 из 10, вархаммер на кончиках пальцев.
              a(href="https://twitter.com/temahuema").disclaimer-popup__link если вы вдруг хотите посоветовать мне что-то, то можете написать в личные сообщения в твиттере, например.





    
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
    noFilterApplied: true,
    gridSetting:1,


    }
 
    },
    computed:{
    currentGrid: function(){
      return this.gridSetting
      }
      },
    
    created(){
        let data = require('../jsons/library.json'); this.books = data;
      
       
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
  position: relative;
  @media (max-width:560px) {width: 99%}
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
 position: relative
}
.disclaimer {cursor: pointer; transition: 0.3s;
text-align: end}
.disclaimer:hover {color: #d8a941; transition: 0.3s}
.disclaimer-popup {
  visibility: hidden;
  bottom:100%;
  right: 0;
 
  position: absolute;
  font-size: 14rem;
  font-weight: normal;
  width: 30%;
  padding: 10rem;
  @media (max-width: 768px) { width: 66%
    
  };
   @media (max-width: 560px) { width: 90%
    
  } }
.disclaimer:hover .disclaimer-popup {
  position: absolute;
  visibility: visible;

  right: 0;
  background-color: #030706;
 
  color: #fffafa;
  
 



  }

.disclaimer-popup__logo { display: flex; justify-content: start;}
.disclaimer-popup__picture {width: 20%}
.disclaimer-popup__link{color:#fffafa;
&:hover{color: #d8a941}}



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
padding-left: 0;
};
cursor: pointer;
@media (max-width: 560px){padding: 0; border-left: none;
&:hover {border-left: none}}

}

.navigation-list__picture-box {height: 20rem; display: flex; justify-content: center;}
.books-list{
    display: grid;
    
    justify-items: center;
    grid-gap: 5rem;
    margin-top: 25rem;
    max-width: 100%;
    overflow: hidden
    
    
}

.mediumGrid{grid-template-columns: 1fr 1fr 1fr 1fr;
@media (max-width: 768px) {grid-template-columns: 1fr 1fr 1fr
      
    };
@media (max-width: 560px) {grid-template-columns: 1fr 1fr}}

.smallGrid {grid-template-columns: 1fr 1fr 1fr;
@media (max-width: 768px) {grid-template-columns: 1fr 1fr
      
    };
@media (max-width: 560px) {grid-template-columns: 1fr}
}

.hugeGrid {grid-template-columns: 1fr 1fr 1fr 1fr 1fr;

@media (max-width: 768px) {grid-template-columns: 1fr 1fr 1fr 1
      
    };
@media (max-width: 560px) {grid-template-columns: 1fr 1fr 1fr}}


.active {
color:#d8a941;
border-left:2px solid #d8a941;
&:first-child{border-left: none};


@media (max-width: 560px) {border-left: none };
}

.books-list__item {height: 100%; width: 100%; }

.open-navigation { 
display: none;


@media (max-width: 560px) {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 10rem;
}}

.navigationListOpened {height: 130rem;
transition: 0.3s; margin-top: 10rem;}



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

.settings--desktop {@media (max-width: 768px) {display: none
      
    };}
.settings--mobile {display: none; @media (max-width: 768px) {display:flex; justify-content: space-around; width: 50%; margin: 0 auto
      
    };}


</style>