<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-date"></i> 图表</el-breadcrumb-item>
                <el-breadcrumb-item>基础图表</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <el-row :gutter="10">
            <el-col :xs="4" :sm="6" :md="8" :lg="12">
                <div class="grid-content bg-purple-light status" style="height: 400px">
                    <div class="header">
                        <i class="icon-star"></i>
                        <h3>集中器总览</h3>
                    </div>
                    <div class="stats">
                        <div class="stat stat2 stat-link">
                            <span class="stat-value" id="crNum">26970</span>
                            集中器总数
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
            <el-col :xs="4" :sm="6" :md="8" :lg="12">
                <div class="grid-content bg-purple status" style="height: 400px">
                   <div class="header">
                        <i class="icon-star"></i>
                        <h3>表计总览</h3>
                    </div>
                    <div class="stats">
                        <div class="stat stat2 stat-link">
                            <span class="stat-value" id="crNum">26970</span>
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

<!--         
                    <div id="meter" class="meter" style="width: 600px;height:400px;"></div>

                     -->
        <el-row :gutter="10">
            <el-col :xs="4" :sm="6" :md="8" :lg="12">
                <div class="grid-content bg-purple-light">
                    <div class="columnChart">
                        <div class="main"></div>
                    </div>
                </div>
            </el-col>
            <el-col :xs="4" :sm="6" :md="8" :lg="12">
                <div class="grid-content bg-purple">
                    4
                </div>
            </el-col>
        </el-row>

    </div>
</template>

<script>
import echarts from 'echarts'
export default {
    components: {
    },
    data: () => ({
        width: 600,
        height: container.clientHeight
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