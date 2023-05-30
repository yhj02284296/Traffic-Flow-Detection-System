<template>
    <div class="container">
        <div class="num">
            <NumShow /> 
        </div>
        <div class="maTa">
            <div class="table maTaCon">
                <PieChart />
            </div>
            <div class="map maTaCon"><!--地图-->
                <Map /> 
            </div>
            <div class="pic maTaCon">
                <div class="word">
                    <div>平台简介：</div>
                    <p>本平台主要用于监测和分析交通流量的，它结合摄像头或其他传感器，对道路、街道或交叉口等交通场景中的车辆和行人进行检测、跟踪和计数。</p>
                    <div>相关技术栈：</div>
                    <p>算法：采用了yolov5实时处理摄像头采集的视频数据，并将处理好的视频保存到nginx搭建的流媒体服务器，以供前端调用。<br>
                       前端：使用了Vue框架，结合element-ui、Echarts实现了对人或车流量数据的图表分析功能。<br>
                       后端：采用了SpringBoot框架，实现数据的接收发送与用户权限管理。</p>
                </div>
            </div>
        </div>
        <div class="line">
            <LineChart />
        </div>
    </div>
</template>
  
<script>
import { reactive, computed, watchEffect, onMounted } from 'vue'
import LineChart from '../components/LineChart.vue'  //引入组件
import PieChart from '../components/PieChart.vue'
import Map from '../components/Map.vue'
import NumShow from '../components/NumShow.vue'

export default {
    //组件名
    name: 'Visualization',
    components: {
        LineChart,    //注册组件
        PieChart,
        Map,
        NumShow,

    },

    setup() {
        let data = reactive({
            
        })


        //生命周期函数，
        //onMounted：在初始化页面完成后执行
        onMounted(() => {
            
        })


        //数据和函数都要返回
        return {
            data,
        }
    },



}
</script>
<style scoped>

/*最外层容器*/
.container {
    background-color: #f1f8f8;
    height: 100%;
    width: 100%;
}

/*上层数据展示*/
.num {
    display: flex;
    height: 17%;
    justify-content: space-between;
    align-items: center;
}


.maTa {
    display: flex;
    height: 37%;
    justify-content: space-between;
    align-items: center;
}

.line {
    height: 45%;
    background-color: #ffffff;
    border-radius: 10px;
    /* 设置一个通用的圆角 */
}


.maTaCon {
    height: 85%;
    background-color: #ffffff;
    border-radius: 10px;
    /* 设置一个通用的圆角 */
}

.map {
    width: 40%;

}


.table {
    width: 30%;

}

.pic {
    width: 28%;
}

.word{
    margin: 20px;
    font-family: SimHei;
    height: 85%;
    overflow:auto
}
.word div{
    font-size: 18px;
    font-weight: bold;
    color: #444;
}

.word p{
    margin-top: 5px;
    margin-bottom: 5px;
    font-size: 16px;
    color: #444;
}

/*宽度小于1350时*/
@media (max-width: 1350px) {}
</style>
  