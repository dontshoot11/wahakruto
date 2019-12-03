<template lang="pug">
  .book-card
    
    
    
    .book-card__picture-box(v-if="!showDescripiton" @click="switchDescription")
      img.book-card__pic(:src=`book.cover`)
    h2.book-card__name(v-if="!showDescripiton" @click="switchDescription") {{book.name}}
    .book-card__info(v-if ="showDescripiton" @click="switchDescription")
      .book-card__info-content
        h2.book-card__name.book-card__name--desctiption {{book.name}}
      
        .book-card__author Автор: {{book.author}}
        .book-card__date Год публикации: {{book.date}}
        .book-card__setting Сеттинг: {{book.setting}}
      
        .book-card__description {{book.description}}
      
        .book-card__fakebutton [нажмите в любом месте, чтобы закрыть]
</template>

<script>
export default {
  props: {
    book: {},
   
  
  },
  data(){return {
    showDescripiton: false,
    
    



  }},

  methods:{
    switchDescription(){this.showDescripiton = !this.showDescripiton},
    
    resetFilter(){this.$emit('resetFilter')}
  }
}
</script>

<style lang="scss" scoped>
.book-card{height: 100%;
width: 100%;
display: flex;

flex-direction: column;
align-items: center;
overflow: auto;
background: #fffafa;
color:#030706;
cursor: pointer;

}
.book-card__info {
  background: #fffafa;
  color: #030706;
  padding: 10rem;
  position: fixed;
  width: 100%;
  height: 100%;
  top:0; 
  left:0;
  background: rgba($color: #030706, $alpha: 0.5);
  z-index: 2;


  

  
  
  

  }

.book-card__info-content {
  position:absolute;
  width: 55%;
  top:50%;
  left:50%;
  transform:translate(-50%, -50%);
  border: 1px solid black;
  background: #fffafa;
  padding: 10rem;
  
  
  @media (max-width: 560px) {
    width: 95%;   height: 95%;
    }}

.book-card__name{font-weight: bold; font-size: 20rem}
.book-card__picture-box{height: 100%; cursor:pointer; overflow: hidden; padding: 25rem; max-height: 550rem; flex-shrink: 1; overflow: hidden; display: flex; align-items: center}
.desctiption{height: 100%;width:100%; cursor: pointer;}
.book-card__description{margin-top: 15rem; 
@media (max-width: 320px) {line-height: 1.1em}


}

.book-card__pic{max-height: 100%;
width: auto;


}

.book-card__fakebutton {cursor: pointer; display: none;
@media (max-width: 560px){display: block; position: absolute; bottom: 0; text-align: center; font-size: 12rem;  width: 100%; color: rgba($color: #000000, $alpha: 0.7)}}



</style>