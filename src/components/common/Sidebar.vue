<template>
    <div class="sidebar">
        <el-menu :default-active="onRoutes" class="el-menu-vertical-demo" theme="dark" unique-opened router>
            <template v-for="item in items">
                <template v-if="item.subs">
                    <el-submenu :index="item.index">
                        <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index">{{ subItem.title }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <i :class="item.icon"></i>{{ item.title }}
                    </el-menu-item>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                items: [
                    {
                        icon: 'el-icon-menu',
                        index: 'basecharts',
                        title: '主页'
                    },
                    {
                        icon: 'el-icon-document',
                        index: '2',
                        title: '档案管理',
                        subs: [
                            {
                                index: 'basetable',
                                title: '区域'
                            },
                            {
                                index: 'vuetable',
                                title: '建筑物'
                            },
                            {
                                index: 'oldcharts',
                                title: '集中器'
                            },
                            {
                                index: '',
                                title: '表计'
                            },
                            {
                                index: '',
                                title: '路由'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-menu',
                        index: '3',
                        title: '抄表管理',
                        subs: [
                            {
                                index: '',
                                title: '基础表格'
                            },
                            {
                                index: '',
                                title: 'Vue表格组件'
                            }
                        ]
                    },  
                    {
                        icon: 'el-icon-setting',
                        index: '4',
                        title: '运行维护',
                        subs: [
                            {
                                index: '',
                                title: '基础表格'
                            },
                            {
                                index: '',
                                title: 'Vue表格组件'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-menu',
                        index: '5',
                        title: '权限管理',
                        subs: [
                            {
                                index: '',
                                title: '基础表格'
                            },
                            {
                                index: '',
                                title: 'Vue表格组件'
                            }
                        ]
                    },                                                              
                    {
                        icon: 'el-icon-date',
                        index: '6',
                        title: '表单',
                        subs: [
                            {
                                index: 'baseform',
                                title: '基本表单'
                            },
                            {
                                index: 'vueeditor',
                                title: '编辑器'
                            },
                            {
                                index: 'markdown',
                                title: 'markdown'
                            },
                            {
                                index: 'upload',
                                title: '文件上传'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: 'drag',
                        title: '拖拽'
                    }
                ]
            }
        },
        computed:{
            onRoutes(){
                return this.$route.path.replace('/','');
            }
        }
    }
</script>

<style scoped>
    .sidebar{
        display: block;
        position: absolute;
        width: 250px;
        left: 0;
        top: 70px;
        bottom:0;
        background: #2E363F;
    }
    .sidebar > ul {
        height:100%;
    }
</style>
