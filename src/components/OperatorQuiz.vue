<template>
<div>
    <div v-if="isQuizStarted">
        <h3>{{operandLeft}} {{operator}} {{operandRight}} </h3>
        <button @click= "selectAnswer(answer)" v-for="(answer,index) of answers" :key="index">{{answer}}</button>
    </div>

    <div v-if="!isQuizStarted">
        <button @click="startQuiz">Start</button>
    </div>

    <button @click="$emit('onBack')">Previous</button>
</div>
</template>

<script>
export default {
    props: ["operator"],
    data() {
        return {
            isQuizStarted: false,
            operandLeft: null,
            operandRight: null,
            answers : [],
            expectedAnswer : null
        };
    },
    methods: {
        selectAnswer(answerSelected){
            if(answerSelected !== this.expectedAnswer){
                alert("wronng answer");
            }
            this.startQuiz();
        },
        startQuiz() {
            this.isQuizStarted = true;
            this.operandLeft = parseInt(Math.random() * 13);
            this.operandRight = parseInt(Math.random() * 13);

            const methods = {
                "+" : (a,b) => a+b,
                "-" : (a,b) => a-b,
                "*" : (a,b) => a*b,
                "/" : (a,b) => a/b,
            }

            const methodYoUse =   methods[this.operator];

            this.answers = [];
            for(let i=0;i<5;i++){
                const answer = methodYoUse(parseInt(Math.random() * 3),parseInt(Math.random() * 3) );
                this.answers.push(answer);
            }

            const expectedAnswer = methodYoUse(this.operandLeft , this.operandRight)
            this.answers[parseInt(Math.random() * this.answers.length) ] = expectedAnswer; 

            this.expectedAnswer = expectedAnswer;
        }
    }
};
</script>

<style>
</style>
