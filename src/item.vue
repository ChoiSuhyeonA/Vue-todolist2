<template>
<div class="items">
    <div class ="item-input">
        <label for = "id">ID</label>
        <input v-model="item.id" placeholder="ID" id="id" >
    </div>
    <div class= "item-input">
        <label for ="name">Name</label>
        <input v-model="item.name" placeholder="Name" id="name">
    </div>

    <div class= "item-input">
        <label for ="available">Available</label>
        <input v-model="item.available"  type="checkbox"  id="available">
    </div>

    <button @click=saveItem>save</button>
    <button v-on:click=deleteItem>delete</button>
   
</div>
    
</template>

<script>

import Item from './classes/item.js'
import {ItemService} from './services/item.service'
export default{
    name : 'Item',
    data(){
        return {
             editable:false,
             item: new Item('','', true) 
        }
    },
    mounted(){
        var id = this.$route.params.id;
        if(id){
            this.editable = true;
            this.item = ItemService.getItem(id);
        }

     },
     methods:{
         saveItem(){
             console.log(this.item)
             if(this.editable){
                 //Save Item
                 ItemService.saveItems();
             }else{
                 // Add item
                 ItemService.addItem(this.item);
             }
             this.$router.push('/home');
         },
         deleteItem(){
             //Delete parm : Item
             ItemService.deleteItem(this.item);
            this.$router.push('/home');    
         }
     }
  

}
</script>


<style scoped>


.item-input{
    margin:2em;
}
label{
    display: inline-block;
    width: 5em;
    margin: 0.5em;
    color: #607d88;
    font-weight: bold;
}
input{
    height: 2em;
    font-size: 1em;
    padding-left: .4em;
    width: 5em;
}
button{
    margin: 20px;
    font-family: Arial;
    font-size: 1em;
    background-color: #eee;
    border:none;
    padding: 5px 10px;
    width:5em;
    border-radius: 4px;
    cursor: pointer;
  
}
button:hover {
    background-color: #cfd8dc;
}
</style>