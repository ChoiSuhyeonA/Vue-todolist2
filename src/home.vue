<template>
    <div class="items">

    <div>    
    <p>
        All : <span> {{items.length}}</span>
    </p>
    <div class="item-line" v-bind:key="item.id" v-for="item in items" v-on:click="updateItem(item.id)">
        <span class= "item-id">{{item.id | uppercase}}</span> {{item.name}}
    </div>
    </div>

    <div>    
    <p>
        Available
    </p>
    <div class="item-line" v-bind:key="item.id" v-for="item in available" v-on:click="updateItem(item.id)">
        <span class= "item-id">{{item.id | uppercase}}</span> {{item.name}}
    </div>
    </div>

    </div>
  
</template>

<script>

import {ItemService} from './services/item.service'
export default{
    name : 'Home',
    data(){
        return {
            items: []
        }
    },
    created(){
        ItemService.getItems();
        this.items = ItemService.items;
    },
    methods:{
        updateItem(id){
           this.$router.push('item/'+id)
        }
    },
    filters:{
        uppercase : function(value){
            if(!value) return ''
            value = value.toString()
            return value.toUpperCase()
        }
    },
    computed:{
        available: function(){
            return this.items.filter(item => item.available);
        }
    }
}
</script>

<style scoped>
    .items{
        margin : 0 0 2em 0;
    }
    .item-line{
        cursor : pointer;
        background-color: #eee;
        margin : .5em;
        padding: .3em 0;
        height: 1.6em;
        border-radius: 4px;
    }
    .item-line:hover{
        color: #607d88;
        background-color: #DDD;
    }
    .item-id{
        display: inline-block;
        font-size: small;
        font-weight: bold;
        color: blue;
        margin: .5em;
        padding:.3em 0;
        height: 1.6em;
        text-align: left;
    }
</style>