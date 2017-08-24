<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-date"></i> 图表</el-breadcrumb-item>
                <el-breadcrumb-item>基础图表</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <!-- <div id="concentrator" class="concentrator" style="width: 600px;height:400px;"></div> -->

        <el-row :gutter="10">
            <el-col :xs="4" :sm="6" :md="8" :lg="12">
                <div class="grid-content bg-purple-light status" style="height: 400px">
                    <div class="header">
                        <i class="icon-star"></i>
                        <h3>集中器总览</h3>
                    </div>
                    <div class="stats">
                        <div class="stat stat2 stat-link">
                            <span class="stat-value" id="crNum">
                                <a href="#/basetable">26970</a>
                            </span>
                            集中器总数
                        </div>

                        <div class="stat stat2 stat-link">
                            <span class="stat-value" id="onNumber">
                                <a href="#/basetable">6084</a>
                            </span>
                            在线数
                        </div>
                    </div>
                    <div class="footer">
                        <div class="stats">
                            <div class="stat stat3 stat-link">
                                <span class="stat-value" id="linkRate">
                                    <a href="#/basetable">22%</a>
                                </span>
                                连通率
                            </div>
                        </div>
                    </div>
                </div>
            </el-col>
            <el-col :xs="4" :sm="6" :md="8" :lg="12">
                <div class="grid-content bg-purple status" style="height: 400px">
                    <div class="header">
                        <i class="icon-star"></i>
                        <h3>表计总览</h3>
                    </div>
                    <div class="stats">
                        <div class="stat stat2 stat-link">
                            <span class="stat-value" id="meterNum">26970</span>
                            表计总数
                        </div>

                        <div class="stat stat2 stat-link">
                            <span class="stat-value" id="onNumber">6084</span>
                            在线数
                        </div>
                    </div>
                    <div class="footer">
                        <div class="stats">
                            <div class="stat stat3 stat-link">
                                <span class="stat-value" id="linkRate">22%</span>
                                连通率
                            </div>
                        </div>
                    </div>
                </div>
            </el-col>
        </el-row>
        <div class="echarts concentrator">
            <IEcharts :option="pie"></IEcharts>
        </div>
        <div class="echarts meter">
            <IEcharts :option="pie"></IEcharts>
        </div>
    </div>
</template>

<script>
import echarts from 'echarts'
import IEcharts from 'vue-echarts-v3/src/lite.vue';
import 'echarts/lib/chart/pie';

export default {
    components: {
        IEcharts
    },
    data: () => ({
        data: [
            { name: '2012', value: 1141 },
            { name: '2013', value: 1499 },
            { name: '2014', value: 2260 },
            { name: '2015', value: 1170 },
            { name: '2016', value: 970 },
            { name: '2017', value: 1450 }
        ],
        line: {
            color: ["#20a0ff", "#13CE66", "#F7BA2A", "#FF4949"],
            title: {
                text: '曲线图'
            },
            xAxis: {
                data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
            },
            yAxis: {},
            series: [
                {
                    name: "销量",
                    type: "line",
                    data: [5, 20, 36, 10, 10, 20]
                }
            ],
            resizable: true
        },
        bar: {
            color: ["#20a0ff", "#13CE66", "#F7BA2A", "#FF4949"],
            title: {
                text: '柱状图'
            },
            xAxis: {
                data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
            },
            yAxis: {},
            series: [
                {
                    name: "销量",
                    type: "bar",
                    data: [5, 20, 36, 10, 10, 20]
                }
            ]
        },
        pie: {
            color: ["#20a0ff", "#13CE66", "#F7BA2A", "#FF4949", "#61a0a8"],
            title: {
                text: '饼状图',
                x: 'center'
            },
            tooltip: {
                trigger: 'item',
                formatter: "{a} <br/>{b} : {c} ({d}%)"
            },
            legend: {
                orient: 'vertical',
                left: 'left',
                data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋"]
            },
            series: [
                {
                    name: '销量',
                    type: 'pie',
                    radius: '55%',
                    center: ['50%', '50%'],
                    data: [
                        { value: 335, name: '衬衫' },
                        { value: 310, name: '羊毛衫' },
                        { value: 234, name: '雪纺衫' },
                        { value: 135, name: '裤子' },
                        { value: 548, name: '高跟鞋' }
                    ],
                    itemStyle: {
                        emphasis: {
                            shadowBlur: 10,
                            shadowOffsetX: 0,
                            shadowColor: 'rgba(0, 0, 0, 0.5)'
                        }
                    }
                }
            ],
            resizable: true

        },
        pie_radius: {
            color: ["#20a0ff", "#13CE66", "#F7BA2A", "#FF4949", "#61a0a8"],
            title: {
                text: '环形图',
                x: 'center'
            },
            tooltip: {
                trigger: 'item',
                formatter: "{a} <br/>{b} : {c} ({d}%)"
            },
            legend: {
                orient: 'vertical',
                left: 'left',
                data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋"]
            },
            series: [
                {
                    name: '销量',
                    type: 'pie',
                    radius: ['40%', '60%'],
                    data: [
                        { value: 335, name: '衬衫' },
                        { value: 310, name: '羊毛衫' },
                        { value: 234, name: '雪纺衫' },
                        { value: 135, name: '裤子' },
                        { value: 548, name: '高跟鞋' }
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
        },
        mix: {
            color: ["#20a0ff", "#13CE66", "#F7BA2A", "#FF4949", "#61a0a8"],
            legend: {
                data: ['步步高', '小天才', 'imoo']
            },
            xAxis: {
                data: ['周一', '周二', '周三', '周四', '周五', '周末']
            },
            yAxis: {},
            series: [
                {
                    name: "步步高",
                    type: "line",
                    data: [15, 20, 26, 30, 40, 27]
                },
                {
                    name: "小天才",
                    type: "bar",
                    data: [5, 30, 36, 10, 34, 20]
                },
                {
                    name: "imoo",
                    type: "bar",
                    data: [35, 40, 30, 50, 60, 40]
                }
            ]
        }
    }),
    mounted() {
    }
}
</script>

<style scoped>
.echarts {
    float: left;
    width: 500px;
    height: 400px;
}

.meter {
    float: right;
}

.status {
    margin-bottom: 20px;
}

.row {
    height: 400px;
}

.header h3 {
    background: #4fc08d;
    color: #fff;
    padding: 10px 15px;
    margin-bottom: 20px;
}

.footer {
    padding-top: 80px;
}

.stats {
    width: 100%;
    display: table;
    padding: 0 0 0 10px;
    margin-top: .5em;
    margin-bottom: 1.9em;
}

.stats .stat {
    display: table-cell;
    width: 40%;
    vertical-align: top;
    font-size: 11px;
    font-weight: bold;
    color: #999;
}

.stats .stat.stat2 {
    width: 50%;
    text-align: center;
}

.stat.stat3 {
    width: 100%;
    text-align: center;
}

.stat-value {
    cursor: pointer;
    display: block;
    margin-top: .55em;
    margin-bottom: .55em;
    font-size: 40px;
    font-weight: bold;
    letter-spacing: -2px;
    color: #444;
}


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

.el-col {
    border-radius: 4px;
}

.bg-purple-dark {
    background: #99a9bf;
}

.bg-purple {
    background: #d3dce6;
}

.bg-purple-light {
    background: #e5e9f2;
}

.grid-content {
    border-radius: 4px;
    min-height: 36px;
}
</style>