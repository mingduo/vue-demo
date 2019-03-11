<template>
    <div id="app">
        <!-- 3、使用：两种命名方式 : 小写-小写；驼峰 -->
        <!--<img alt="Vue logo" src="./assets/logo.png">-->
        <HelloWorld msg="Welcome to Your Vue.js App"/>
        <!--<child-component :propFromParent="propFromParent"-->
        <!--@propFromChild="propFromChild"></child-component>-->
        <br>
        <!--<div>我是父组件：正在接收子组件的值：</div>-->
        <!--<div>{{ propFromChildData.msg }}</div>-->

        <br>
        <!-- elementUI 组件 -->
        <!--<ele-component></ele-component>-->

        <br>
        <!-- elementUI Form 组件 -->
        <!--<div>elementUI Form 组件</div>-->
        <br>
        <!--<ele-form-component></ele-form-component>-->
    </div>
</template>

<script>
    // 功能文件、配置、组件、接口引入
    // 组件引入步骤：
    // 1、import 引入
    import ChildComponent from './components/childComponent'
    import HelloWorld from './components/HelloWorld.vue'
    import EleComponent from './components/eleComponent'
    import EleFormComponent from './components/eleFormComponent'

    export default {
        name: 'app',
        // 2、生命组件选项
        components: {
            HelloWorld, ChildComponent, EleComponent, EleFormComponent
        },
        data() {
            return {
                propFromParent: '这条消息是父组件动态传递给子组件的',
                propFromChildData: ''
            }
        },

        methods: {
            propFromChild(data) {
                this.propFromChildData = data
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
