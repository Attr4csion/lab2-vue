<template>
    <div>
        <p>{{ data.header }}</p>
        {{ data.persons[0].id+' '+data.persons[0].name+' '+data.persons[0].surname }}
        {{ data.persons[1].id+' '+data.persons[1].name+' '+data.persons[1].surname }}
        {{ data.persons[2].id+' '+data.persons[2].name+' '+data.persons[2].surname }}
        {{(data.persons[0].donate+ data.persons[1].donate+data.persons[2].donate)}}
    </div>
</template>

<script>
export default{
    data(){
        return{
            data:{
            header:'список приглашенных',
            persons:[
                {id:0,name:'Иван',surname:'Иванов',donate:300},
                {id:1,name:'Петр',surname:'Петров',donate:200},
                {id:2,name:'Александр',surname:'Александров',donate:400},]
            }
        }
    }
}
</script>

<style scoped>

*{
max-width: 100%;
font-size: 18px;
}
</style>