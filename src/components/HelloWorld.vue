<template>
    <!-- 注意点 -->
    <!-- template里面最多只能有一个父级元素 -->
    <div>
        <!-- 原生DOM -->
        <template v-if="false">
            <h3>我是原生DOM</h3>
            <P>我也是原生DOM</P>
        </template>
        <!-- 模板解析 -->
        <template v-if="false">
            <!-- 动态渲染变量、javaScript表达式 -->
            <!--<div>Message：{{ msg }}</div>-->
            <!-- (双向绑定) -->
            input值是：<span>{{ inputValue }}</span><br>
            input计算之后的值是：<span>{{ computedInputValue }}</span><br>
            <input type="text" v-model="inputValue"/>

            <!-- 指令(v- 前缀的特殊特性)：
            v-html、v-if、v-else、v-else-if、v-show、v-bind、v-on、v-for、v-model -->
            <!--<div v-html="vHtml"></div>-->
            <!--<div v-show="false">v-show：DOM已经加载，但是，显式隐藏了</div>-->
            <!--<div v-if="false">v-if：我跟v-show不同，我为false时，根本不会加载</div>-->
            <!--<ul>-->
            <!--<li v-for="(item,i) in vFor" :key="i">{{ item }}</li>-->
            <!--</ul>-->
            <!-- v-bind 为DOM属性绑定变量 -->
            <!--<a :href="vBindHref">{{ vBindHref }}</a>-->
            <!-- v-on 事件绑定，支持所有原生事件 -->
            <!-- 修饰符：.stop .prevent .capture .self .once .passive -->
            <!--<button @click.stop="handleClick()">为按钮绑定点击事件</button>-->
        </template>

        <!-- class 与 style绑定 -->
        <template v-if="false">
            <!-- 方式一：变量绑定 -->
            <div ref="dddd"
                 class="class-default"
                 @click="toggleClassDefaultActive"
                 v-bind:class="{'class-default-active': classDefaultActive}">通过变量控制
            </div>
            <br>
            <!-- 方式二：对象绑定 -->
            <div class="class-default"
                 @click="toggleClassDefaultObject"
                 :class="classDefaultObject">通过对象绑定控制
            </div>
        </template>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        /** data用于管理实例内所有数据
         * 必须是一个函数，最后返回一个包含所有数据的对象
         *  @return Object {}
         * */
        data() {
            return {
                msg: 'this is a message',
                inputValue: 'hello',
                vFor: ['张三', '李四', '王五', '孙六'],
                vHtml: '<h3>我是v-html渲染出来的，还可以覆盖DOM里面的内容</h3>',
                vBindHref: 'https:www.baidu.com', // 'http://www.yunzhangfang.com/',

                classDefaultActive: true,
                classDefaultObject: {
                    'class-default-active': false
                }
            }
        },
        methods: {
            handleClick(msg) {
                debugger
                alert(msg || '点击了按钮，没有传递参数')
            },

            toggleClassDefaultActive() {
                console.log(this)
                console.log(this.$el)
                this.classDefaultActive = !this.classDefaultActive
            },

            toggleClassDefaultObject() {
                this.classDefaultObject = {'class-default-active': !this.classDefaultObject['class-default-active']}
            }
        },
        // 计算属性
        // 根据现有变量通过一些计算输出新的变量
        computed: {
            computedInputValue() {
                return this.inputValue.split('')
            }
        },
        // 生命周期(常用)
        mounted() {
            // 做一些初始化操作、数据初始化...
        },
        beforeDestroy() {
            // 在组件销毁之前处理逻辑
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .class-default {
        width: 200px;
        height: 100px;
        background-color: brown;
    }

    .class-default-active {
        background-color: blueviolet;
    }
</style>
