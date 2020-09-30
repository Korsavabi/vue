<template>
    <!-- <div>
        <ul>
            <li><img src="https://cdnimg.rg.ru/img/content/174/33/99/bangkok_d_850.jpg" alt="" width="250px"></li>
            <li>Lorem ipsum dolor sit amet consectetur adipisicing elit</li>
            <li>Error, cupiditate! Cupiditate nostrum magni recusandae eius maxime dolore illum eaque obcaecati ipsa cumque, 
                pariatur laudantium delectus quis voluptatibus velit quasi tenetur!</li>
        </ul>
        <Button>Редактировать</Button>
    </div> -->

    
            <!-- <ul>
                <li v-for="content in contented" :key="content"><img :src="content.images" alt="" width="250px">
            <h5>{{content.heading}}</h5>
            <p>{{content.text}}</p></li>
            </ul> -->
            

    <div container>
        <div class="row">     
            <div class="row">
                <div class="col s12">                    
                    <input type="text" v-model="search" placeholder="Search" class="input1">
                </div>                          
            
            </div>

            <div class="input-field col s4">
                    <b>Картинка:</b> <img :src="newImeges" alt="" width="250px">
                    <input type="imegas" v-model="newImeges" placeholder="URL" class="input1">
                </div>
 
                <div class="input-field col s4">
                    <b>Заголовок:</b> {{newHeading}}
                    <input type="text" v-model="newHeading" placeholder="Heading: " class="input1">
                </div>

                <div class="input-field col s4">
                    <b>Краткое описание:</b>
                    <textarea type="text" v-model="newText" placeholder="Short description: " class="input1" maxlength="70" />
                </div>

                <div class="input-field col s4">
                    <b>Полное описание:</b>
                    <textarea type="text" v-model="newTextTwo" placeholder="Full description: " class="input1" />
                </div>
 
                <div class="col s4">
                    <a @click="addItems" class="waves-effect waves-light btn" style="margin-top: 15px">Add new</a>
                </div>

        </div>
        
        <div class="row">
            <teg-blog-items v-for="(content, index) in searchItems" :key="content"
             :content="content" :index="index" @removePost="removeItems"></teg-blog-items>
        </div>
        
    </div>
</template>

<script>

import BlogItems from './BlogItems'

export default {
    data () {
        return {

            contented: [
                {images: "https://kakzachem.com/wp-content/uploads/2020/05/gol-200-1170x650.jpg", heading: "Звездные детки, которые отличаются необычным внешним видом", text: "Современные родители в воспитании своих детей руководствуются принципом", 
                texttwo:"Современные родители в воспитании своих детей руководствуются принципом – не стоит ограничивать их возможности самовыражения, чтобы они выросли самостоятельными и гармонично развитыми личностями. Впрочем, иногда такая вседозволенность достигает крайней черты."},
                {images: "https://kakzachem.com/wp-content/uploads/2020/05/depositphotos_8190924_xl-2015-825x510.jpg", heading: "«Тебе же пенсию платят!» — ответ матери одной очень «умной» дочери", text: "У меня есть подруга, которая, так же как и я, проживает в Москве", 
                texttwo:"У меня есть подруга, которая, так же как и я, проживает в Москве. Она в столице недавно, переехала после замужества. Семья у нее не бедствует, муж прилично зарабатывает. Имеют хороший"},
                {images: "https://kakzachem.com/wp-content/uploads/2020/05/13-91-768x438.jpg", heading: "Пять проектов, которые показывают мощь Советского Союза", text: "Развитие военной и космической индустрии шло быстрыми темпами, что вылилось", 
                texttwo:"Несмотря на всю критику советского периода времени, СССР получил статус сверхдержавы и успешно конкурировал с Соединенными Штатами Америки не зря. Развитие военной и космической индустрии шло быстрыми темпами, что вылилось"}
            ],
            newImeges: '',
            newHeading: '',
            newText: '',
            newTextTwo: '',
            search: ''
        }
    },
    components: {      
      'teg-blog-items': BlogItems
    },
    methods: {
        removeItems(index){
            this.contented.splice(index, 1);
        },
        addItems(){

            if(this.newImeges !="" && this.newHeading !="" && this.newText != "" && this.newTextTwo !=""){
                this.contented.push({images: this.newImeges, heading: this.newHeading, text: this.newText, texttwo: this.newTextTwo});
                this.newImeges = "";
                this.newHeading = "";
                this.newText = "";
                this.newTextTwo = "";
            }

        }
    },
    computed: {
        searchItems(){
            return this.contented.filter (content => content.heading.startsWith(this.search))
        }
    }
    
}
</script>

<style>
.input1::-webkit-input-placeholder       {opacity: 1; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1::-moz-placeholder                {opacity: 1; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1:-moz-placeholder                 {opacity: 1; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1:-ms-input-placeholder            {opacity: 1; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1:focus::-webkit-input-placeholder {opacity: 0; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1:focus::-moz-placeholder          {opacity: 0; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1:focus:-moz-placeholder           {opacity: 0; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
.input1:focus:-ms-input-placeholder      {opacity: 0; transition: opacity 0.3s ease; color: rgba(0, 68, 255, 0.527);}
textarea{
    resize: none;
    
}
</style>