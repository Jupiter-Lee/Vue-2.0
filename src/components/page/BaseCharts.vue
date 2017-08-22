<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-date"></i> 图表</el-breadcrumb-item>
                <el-breadcrumb-item>基础图表</el-breadcrumb-item>
            </el-breadcrumb>
        </div>

        <div class="row">
            <div class="col-md-6" style="background-color: #dedef8; box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">

                <div id="concentrator" class="concentrator" style="width: 600px;height:400px;"></div>

            </div>
            <div class="col-md-6" style="background-color: #dedef8; box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">

                <div id="meter" class="meter" style="width: 600px;height:400px;"></div>

            </div>
            <!-- 
                <div class="crData"></div>
                <div class="meterData"></div>
     -->

        </div>
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
#concentrator {
    background: aliceblue;
}

#meter {
    background: aliceblue;
}

.rate {
    width: 100%;
    height: auto;
}

.concentrator {
    margin-bottom: 10px;
}

.meter {
    margin-top: 10px;
}

.crData {
    width: 300px;
    height: 400px;
    float: right;
    border: solid #aaaaaa 1px;
}

.meterData {
    width: 300px;
    height: 400px;
    float: right;
    border: solid #aaaaaa 1px;
}
</style>