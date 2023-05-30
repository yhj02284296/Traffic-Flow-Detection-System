<template>
    <div class="index">
        <div class="title"><h1 class="title1">基于深度学习的交通流量监测系统</h1>
        <div class="sign1 card">
            <input placeholder="name" type="text" v-model="data.name">
            <input placeholder="password" type="password" v-model="data.password" @keydown.enter="sign">
            <input class="buttom" type="submit" value="登  录" @click="sign">
            <p>仅作为展示，非实际部署版本。</p>
        </div>
    </div>
    </div>
</template>
  
<script>
import { reactive, computed, watchEffect, onMounted } from 'vue'
import axios from 'axios'          //引入axios
import { ElMessage } from 'element-plus'
import { useRouter } from "vue-router";
export default {
    //组件名
    name: 'Login',
    setup() {
        const router = useRouter()
        let data = reactive({
            name: "",
            password: "",

        })

        function sign() {
            axios.post('api/user/login', {
                "name": data.name,
                "password": data.password,
            }).then(function (value) {
                if (value.data.status == 200) {
                    window.localStorage.setItem('name', value.data.name)
                    window.localStorage.setItem('usertype', value.data.usertype)
                    window.localStorage.setItem('remark', value.data.remark)
                    window.localStorage.setItem('avatar', value.data.avatar)
                    window.localStorage.setItem('phone', value.data.phone)
                    router.push("/");

                    ElMessage({
                        message: '登录成功',
                        type: 'success',

                    })
                }else if(value.data.status == 1){
                    ElMessage({
                        message: '密码错误',
                        type: 'warning',

                    })
                }else if(value.data.status == 2){
                    ElMessage({
                        message: '用户名不存在',
                        type: 'warning',

                    })
                }


            }).catch(function (reason) {
                console.log(reason)
            })

        }




        //生命周期函数，
        //onMounted：在初始化页面完成后执行
        onMounted(() => {

        })


        //数据和函数都要返回
        return {
            data,
            sign
        }
    },



}
</script>


<style scoped>
.sign1 {
    width: 400px;
    height: 320px;
    font-family: MiSans;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-left: 50px;
}
input {
    outline: 0;
    background: #f2f2f2;
    width: 72%;
    border: 0;
    margin: 0 0 15px;
    padding: 12px;
    box-sizing: border-box;
    font-size: 22px;
}
.buttom {
    font-family: MiSans;
    outline: 0;
    background: #4CAF50;
    width: 72%;
    height: 50px;
    border: 0;
    color: #FFFFFF;
    font-size: 22px;
    cursor: pointer;
    margin-top: 20px;
}
.buttom:hover {
    font-size: 24px;
    background: #43A047;
}
p {
    color: #333;
}


.index{
    /* background-color: #7499ce; */
    background-image: url("../assets/login-background.jpg");
    align-items: center;
    display: flex;
    justify-content: center;
    background-size: cover;
}
.title{
    align-items: center;
    display: block;
    justify-content: center;
   
}
.title1{
    margin: 30px;
}

</style>
  


