<template>
    <div>
                    
                <img :src="user.avatar" alt="" width="150px" style="border-radius: 15%;">
                <h3>{{user.name}}</h3>   
                <input v-model="user.avatar" placeholder="URL" type="images" :disable="!isEdit" :class="{view: !isEdit}">        
                <input v-model="user.name" placeholder="Name" type="text" ref="name" :disable="!isEdit" :class="{view: !isEdit}">
                <button @click="isEdit = !isEdit" v-if="!isEdit">Редактировать</button>
                <button @click="save" v-else-if="isEdit">Сохранить</button>
                <button v-if="isEdit" @click="isEdit = false">Отмена</button>   
        
             
        
        
    </div>
</template>

<script>
export default {
    data (){
        return {
            isEdit: false,
            user: {name: 'Petr Petrov', avatar:'https://klike.net/uploads/posts/2018-06/1528720172_1.jpg'},
            name: "",
            avatar: ""



        }
    },
    methods: {
        save(){
            this.user.name = this.$refs['name'].value;            
            this.isEdit = !this.isEdit;
        }
    }
}
</script>

<style>
.view {
  border-color: transparent;
  background-color: initial;
  color: initial;
  font-weight: 600;
  font-size: 25px;
  display: none;  
  
}

</style>