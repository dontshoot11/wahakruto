<template lang="pug">
  .book-card
    h2.book-card__name {{book.name}}
    
    
    .book-card__picture-box(v-if="!showDescripiton" @click="switchDescription")
      img.book-card__pic(:src=`book.cover`)
    .desctiption(v-if ="showDescripiton" @click="switchDescription")  {{book.description}}
</template>

<script>
export default {
  props: {
    book: {},
    isFiltered: Boolean
  
  },
  data(){return {
    showDescripiton: false,
    
    



  }},
  computed:{
    isFilterApplied: function(){
      return this.isFiltered
      }
      },
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
overflow: auto;}
.book-card__name{font-weight: bold; font-size: 20rem}
.book-card__picture-box{height: 100%; cursor:pointer; overflow: hidden;}
.desctiption{height: 100%;width:100%; cursor: pointer;}
.book-card__setting{cursor:pointer}
.book-card__pic{max-height: 100%;
width: auto

}



</style>