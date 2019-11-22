<template lang="pug">
.library
    h2.setting(v-if = "isFiltered") {{setting}}
    button(@click="resetFilter" v-if = "isFiltered") назад
        
    ul.books-list
        li.books-list__item(v-for = "book in books" :isFiltered="isFiltered")
            book(:book="book" @filterBySetting="filterBySetting" :isFiltered="isFiltered")
    
</template>

<script>
import book from "../components/book"

export default {
    components: {book},
    data(){return{
    books:[],
    setting:'',
    isFiltered: false
    }
 
    },
    created(){
        let data = require('../jsons/library.json'); this.books = data
    },
    methods: {
        filterBySetting(book){
            this.books = this.books.filter(books => books.setting === book);
            this.setting = book;
            this.isFiltered = true},
        resetFilter(){
            let data = require('../jsons/library.json'); this.books = data;
            this.isFiltered=false;
            this.setting="";
            
        }
    }

}
</script>

<style lang="scss" scoped>
.books-list{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    justify-items: center
    
}

.books-list__item {height: 500rem; width: 100%}
</style>