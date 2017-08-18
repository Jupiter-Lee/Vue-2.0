<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-date"></i> 图表</el-breadcrumb-item>
                <el-breadcrumb-item>基础图表</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
    
        <div id="concentrator" class="concentrator" style="width: 600px;height:400px;"></div>
        <div id="meter" class="meter" style="width: 600px;height:400px;"></div>
    
    </div>
</template>

<script>
import Schart from 'vue-schart';
import echarts from 'echarts'
export default {
    components: {
        Schart
    },
    data: () => ({
    }),
    mounted() {
        var concentrator = echarts.init(document.getElementById('concentrator'));
        var meter = echarts.init(document.getElementById('meter'));
        var option01 = {
            title: {
                text: '集中器情况',
                subtext: '在线情况',
                x: 'center'
            },
            tooltip: {
                trigger: 'item',
                formatter: "{a} <br/>{b} : {c} ({d}%)"
            },
            legend: {
                orient: 'vertical',
                left: 'left',
                data: ['在线', '离线']
            },
            series: [
                {
                    name: '访问来源',
                    type: 'pie',
                    radius: '55%',
                    center: ['50%', '60%'],
                    data: [
                        { value: 335, name: '在线' },
                        { value: 135, name: '离线' }
                    ],
                    itemStyle: {
                        emphasis: {
                            shadowBlur: 10,
                            shadowOffsetX: 0,
                            shadowColor: 'rgba(0, 0, 0, 0.5)'
                        }
                    }
                }
            ]
        };
        var option02 = {
            title: {
                text: '表计情况',
                subtext: '在线情况',
                x: 'center'
            },
            tooltip: {
                trigger: 'item',
                formatter: "{a} <br/>{b} : {c} ({d}%)"
            },
            legend: {
                orient: 'vertical',
                left: 'left',
                data: ['在线', '离线']
            },
            series: [
                {
                    name: '访问来源',
                    type: 'pie',
                    radius: '55%',
                    center: ['50%', '60%'],
                    data: [
                        { value: 335, name: '在线' },
                        { value: 135, name: '离线' }
                    ],
                    itemStyle: {
                        emphasis: {
                            shadowBlur: 10,
                            shadowOffsetX: 0,
                            shadowColor: 'rgba(0, 0, 0, 0.5)'
                        }
                    }
                }
            ]
        };
        concentrator.setOption(option01)
        meter.setOption(option02)
    }
}
</script>

<style scoped>
.schart {
    max-width: 600px;
    margin: 0 auto;
    display: inline-block;
}

.content-title {
    clear: both;
    font-weight: 400;
    line-height: 50px;
    margin: 10px 0;
    font-size: 22px;
    color: #1f2f3d;
}
</style>