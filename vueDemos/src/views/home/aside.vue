<template>
    <div class="aside-wrap">
        <div class="aside-top flex-wrap j-between">
            <p>测试案例</p>
            <i class="el-icon-s-fold"></i>
        </div>
        <el-menu
            router
            default-active="2"
            class="el-menu-vertical-demo"
            @open="handleOpen"
            @close="handleClose">
            
            <template v-for="(item, index) in contentRouter" >
                <el-submenu  v-if="item.children" :index="item.name" :key="index">
                    <template slot="title">
                        <i class="el-icon-location"></i>
                        <span>{{item.meta.title}}</span>
                    </template>
                    <el-menu-item-group>
                        <el-menu-item  v-for="(sub,index2) in item.children" :key="index2" :index="item.path+'/'+sub.path">
                            {{sub.meta.title}} {{item.path+'/'+sub.path}}
                        </el-menu-item>
                    </el-menu-item-group>
                </el-submenu>
                <el-menu-item v-else :index="item.path" :key="index">
                    <i class="el-icon-setting"></i>
                    <span slot="title">{{item.meta.title}} {{item.path}}</span>
                </el-menu-item>
            </template>
        </el-menu>
    </div>
</template>

<script>
import {routes} from '../../router/index';
export default {
    data(){
        return{
            contentRouter:routes[0].children
        }
    },
    mounted(){
        console.log("contentRouter",this.contentRouter)
    },
    methods:{
        handleOpen(){

        },
        handleClose(){

        }
    }
}
</script>

<style lang="scss">
.aside-wrap{
    width: 240px;
    box-sizing: border-box;
    .aside-top{
        padding: 16px 16px 20px;
        height: 56px;
        background: #000000;
        box-sizing: border-box;
        color: white;
    }
}
</style>