<template>
    <div class="contains">
        <div class="head">
            <button @click="changeType(1)">列表视图</button>
            <button @click="changeType(2)">网格视图</button>
            <input type="text" placeholder="搜索文件" v-model="fileName" @input="searchFile">
        </div>
        <ul :class="[type==1 ? '' : 'flex']">
            <li :class="[type==1 ? '' : 'flex']" v-for="(v, i) in newList" :key="i">{{v}}</li>
        </ul>
    </div>
</template>


<script>
    export default{
        data(){
            return {
                type: 1,
                fileName: '',
                newList: []
            }
        },
        props: ["list"],
        created(){
            this.list.sort()
            this.list.sort((a, b) => {
                return a.length - b.length
            })
            this.newList = this.list;
        },
        methods: {
            changeType(i){
                this.type = i
            },
            searchFile(){
                this.newList = this.list.filter(item => {
                    let reg = new RegExp(this.fileName, 'g')
                    console.log(reg)
                    return reg.test(item)
                })
                console.log(this.newList)
            }
        }
    }
</script>

<style scoped>
    ul{
        list-style: none;
        margin: 0;
        padding: 0;
        padding-top: 10px;
    }
    ul li{
        border-bottom: 1px solid gainsboro;
        line-height: 50px;
    }
    ul.flex{
        display: flex;
        flex-wrap: wrap;
    }
    ul li.flex{
        width: 70px;
        height: 70px;
        border: 1px solid gainsboro;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        line-height: 70px;
        text-align: center;
        margin-right: 10px;
        margin-bottom: 10px;
    }
</style>