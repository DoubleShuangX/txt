<template>
    <div class="contains">
        <FileManage :list="list" />
    </div>
</template>


<script>
    import FileManage from '../components/file-manage'
    export default{
        components: {
            FileManage
        },
        data(){
            return {
                list: ['test21.txt', 'testtest2.txt', 'testtest3.txt', 'test3.txt', 'test4.txt' ]
            }
        }
    }
</script>

<style scoped>

</style>