<template>
    <div>
        <div v-for="(task,index) in tasks" :key="index">
            <p :class="{IsDone:isDone[index],error:hasError[index]}">{{ task.question }}</p>
            <div v-for="(answer,numb) in task.answers" :key="numb" >
                {{ answer }}
                <input class="radio" type="radio" name="quest" @click="checkRadio(numb,task.right,index)">
            </div>
            

        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            tasks:[
	{
		question: 'Вопрос 1',
		answers: [
			'Ответ 1',
			'Ответ 2',
			'Ответ 3',
			'Ответ 4',
			'Ответ 5',
		],
		right: 3, // номер правильного ответа
	},
	{
		question: 'Вопрос 2',
		answers: [
			'Ответ 1',
			'Ответ 2',
			'Ответ 3',
			'Ответ 4',
			'Ответ 5',
		],
		right: 1, // номер правильного ответа
	},
	{
		question: 'Вопрос 3',
		answers: [
			'Ответ 1',
			'Ответ 2',
			'Ответ 3',
			'Ответ 4',
			'Ответ 5',
		],
		right: 5, // номер правильного ответа
	},
],
    currentAnswer:'',
    isDone:[],
    hasError:[]

        }
    },
    methods:{
        checkRadio(numb,Taskvalue,index){
            this.currentAnswer=numb+1
            if(this.currentAnswer == Taskvalue){
				this.hasError[index] = false
                this.isDone[index] = true
            }
			else {
				this.isDone[index] = false
				this.hasError[index] = true
			}
        }
    }
}
</script>

<style>
p{
	max-width: 300px;
}
.IsDone{
    border:2px solid green
}
.error{
	border:2px solid red
}
.radio{
	cursor:pointer
}
</style>