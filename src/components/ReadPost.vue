<template>
    <div>
        <img :src="content.images" alt="" width="525px">
        <h3 style="text-align: center;">{{content.heading}}</h3>
        <p>{{content.texttwo}}</p>

                <input v-model="content.images" placeholder="URL" type="images" :disable="!Edit" :class="{view: !Edit}">        
                <input v-model="content.heading" placeholder="heading" type="text" ref="heading" :disable="!Edit" :class="{view: !Edit}">
                <input v-model="content.text" placeholder="Short description:" type="text" ref="text" maxlength="70" :disable="!Edit" :class="{view: !Edit}">
                <input v-model="content.texttwo" placeholder="Full description:" type="text" ref="texttwo" :disable="!Edit" :class="{view: !Edit}">
                <button @click="Edit = !Edit" v-if="!Edit">Редактировать</button>
                <button @click="save" v-else-if="Edit">Сохранить</button>
                <button v-if="Edit" @click="Edit = false">Отмена</button>   
    </div>
</template>

<script>
export default {
    props: ["content"],
     data (){
        return {
            Edit: false



        }
    },
    methods: {
        save(){
            this.content.heading = this.$refs['heading'].value; 
            this.content.text = this.$refs['text'].value;
            this.content.texttwo = this.$refs['texttwo'].value;            
            this.Edit = !this.Edit;
        }
    }
}
</script>

