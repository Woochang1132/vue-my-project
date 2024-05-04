<template>
    <div>
        X : <input type="text" v-model.number = "state.x" /><br/>
        결과 : {{ state.result }}
    </div>
</template>

<script>
import {watch, reactive} from "vue";

export default{
    name : "Calc6",
    setup(){
        const state = reactive({x : 0, result : 0});
        // reactive 내부 변수에 반응성을 부여하면서 watch 활용하기 위해서는
        // getter 함수 형식을 활용한다.
        watch(() => state.x, (current, old) => {
            console.log(`${old} ==> ${current}`);
            state.result = current * 2;
        })
        return {state}
    }
}
</script>