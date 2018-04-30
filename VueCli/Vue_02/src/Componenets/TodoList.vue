<template>
    <section>
        <ul>
            <li v-for="item in todoItems" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{item}}
                <span class="removeBtn" type="buttn" v-on:click="removeItem(item,index)">
                    <i class="fa fa-trash-o" aria-hidden="true">X</i>
                </span>
            </li>

        </ul>
    </section>
</template>

<script>
    export default{
        data() {
            return {
                todoItems:[]
            }
        },

        created() {
            if(localStorage.length > 0 ) {
                for(var i = 0 ; i <localStorage.length; i++){
                    this.todoItems.push(localStorage.key(i));
                }
            }

        },
        methods:{
            removeItem (obj,idx) {

                this.todoItems.splice(idx,1);
                localStorage.removeItem(obj);
            }
        }
    }
</script>

<style>
    ul{
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0px;
        text-align: left;
    }
    li{
        display: flex;
        min-height:  50px;
        height: 50px;
        line-height: 50px;
        margin:0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }

    .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }

    .removeBtn{
        margin-left:auto;
        color : #de4343;
    }

</style>