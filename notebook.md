## Notebook in FE

格式化构造函数内容
`function zzz(obj) {
	let str = "";
	for (let key in obj) {
		str += 'this.' + key + ' = "";\n'
	}
	return str;
 }`

1. 竖直方向边距自适应：{
  使用占位div+负margin，百度logo部分
	HTML：<div class="content">
				<div class="cont">
					<div class="con">
						<div class="bd_logo">
							<img class="bdlogo" src="https://www.baidu.com/img/bd_logo1.png" alt="baidu logo"/>
						</div>
						……
	CSS:	`.content {
				position: absolute;
				width: 100%;
				height: 100%;
				text-align: center;
				top: 0;
			}

			.cont {
				position: relative;
				top: 38.2%;
				text-align: center;
			}

			.con {
				position: relative;
				text-align: center;
				top: -191px;
			}

			.bd_logo {
				margin: auto;
				clear: both;
				margin-top: 0;
			}

			.bdlogo {
				width: 270px;
				margin-bottom: 25px;
			}
}

2. 带三角的对话框: {
  使用<em></em> + <i></i>
	HTML:	<div class="setting_menu">
				<div class="gap">
					<em></em>
					<i></i>
				</div>
				<div class="menu">
					<a class="menu_item search_setting">搜索设置</a>
					<a class="menu_item senior">高级搜索</a>
					<a class="menu_item predict">关闭预测</a>
					<a href="http://i.baidu.com/my/history?from=ps" class="menu_item history">搜索历史</a>
				</div>
			</div>
	CSS:	.menu {
				border: solid 1px #d1d1d1;
				box-shadow:1px 1px 5px #d1d1d1;
				margin-top: -1px;
			}

			.gap {
				width: 0;
			    height: 0;
			    font-size: 0;
			    line-height: 0;
			    display: block;
			    position: absolute;
			    top: -10px;
			    left: 50%;
			    margin-left: -5px;
			}

			.gap em, .gap i {
				width: 0;
			    height: 0;
			    font-size: 0;
			    line-height: 0;
			    display: block;
			    position: absolute;
			    border: 5px solid transparent;
			    border-style: dashed dashed solid;
			}

			.gap em {
				border-bottom-color: #d8d8d8;
			    top: -1px;
			}

			.gap i {
				border-bottom-color: #fff;
			    top: 0;
			}
}

3. 消除子元素inline-block间距 {
	父级元素设置 {
		font-size: 0;
		-webkit-text-size-adjust:none；
		}
}

4. css类命名规则: {
	id
		页头：header

		登录条：loginbar

		标志：logo

		侧栏：sidebar

		广告：banner

		导航：nav

		子导航：subnav

		菜单：menu

		子菜单：submenu

		搜索：search

		滚动：scroll

		页面主体：main

		内容：content

		标签页：tab

		文章列表：list

		提示信息：msg

		小技巧：tips

		栏目标题：title

		加入：joinus

		指南：guild

		服务：service

		热点：hot

		新闻：news

		下载：download

		注册：regsiter

		状态：status

		按钮：btn

		投票：vote

		合作伙伴：partner

		友情链接：friendlink

		页脚：footer

		版权：copyright
	class
		外　套：　　wrap

		主导航：　　mainnav

		子导航：　　subnav

		页　脚：　　footer

		整个页面：　content

		页　眉：　　header

		页　脚：　　footer

		商　标：　　label

		标　题：　　title

		主导航：　　mainbav（globalnav）

		顶导航：　　topnav

		边导航：　　sidebar

		左导航：　　leftsidebar

		右导航：　　rightsidebar

		旗　志：　　logo

		标　语：　　banner

		菜单内容1： menu1content

		菜单容量：　menucontainer

		子菜单：　　submenu

		边导航图标：sidebarIcon

		注释：　　　note

		面包屑：　　breadcrumb(即页面所处位置导航提示）

		容器：　　　container

		内容：　　　content

		搜索：　　　search

		登陆：　　　Login

		功能区：　　shop(如购物车，收银台)

		当前的　　　current
}

5. 具有title属性的元素，鼠标悬停时会显示title的值 {，如
		<span title="test">
    		just test
    	</span>
    	悬停在“just test”会显示“test” }

6. 对象有多个属性一定要记得加逗号“,” {妈蛋！！
	var app5 = new Vue({
	 	el: '#app-5',
	 	data: {
	    	message: 'hello vue!'
	  	}, //这里啊！！！！逗号啊！！！
	  	methods: {
	      reverseMessage: function () {
	        this.message = this.message.split('').reverse().join('')
	      }
	    }
	})
}

7. Vue插值HTML时应使用指令：v-html=“自定义名称” {，元素内无需再设置{{ html }}
	// html部分
	<div id="creatHTML">
        <div v-html="custom"></div> //div内部无需再设置{{}}
    </div>

    // js部分
    var html = new Vue({
		el: '#creatHTML',
		data: {
			custom: "<p>This is a created HTML.</p>"
		}
	})
}

8. Vue v-bind绑定class时，如果属性带有‘-’，要在整个属性名外加引号 {
	Html中使用  v-bind:class="{ active: isActive, 'text-danger': hasError }">
	或js中使用
		classObject: {
				active: false,
				'text-danger': true
		}
	//  text-danger 都需要加“”
	以上结果都会渲染为<div class="text-danger"></div>
}

9. Vue v-if指令若直接写了表达式，需要在js中new Vue({ el: '#condition' })，才能生效。 {
	Html:  //原则是if后的语句为true时，渲染本元素
	<div id="condition">
        <div v-if="Math.random() > 0.7">>0.7</div>
        <div v-else-if="Math.random() > 0.3">0.3~0.7</div>
        <div v-else> <0.3 </div>
    </div>
    js:
    var testcondition = new Vue({
		el: '#condition'
	})
}

10. Vue v-show始终渲染元素,只操作元素dispaly属性(true时‘’,false时‘none’),v-if真渲染or不渲染

11. ElementUI <el-table :data="someData"> 为<el-table-column>绑定属性，需要<template scope="scope"><el :id="scope.row.someAttr">...{
    <el-table border height="440" :data="shopcarts" class="table table-cdetail table-hover">
		<el-table-column prop="shopName" label="店铺名称"></el-table-column>
		<el-table-column prop="buyName" label="客户姓名"></el-table-column>
		<el-table-column prop="buyPhone" label="客户电话"></el-table-column>
		<el-table-column prop="totalPrice" label="订单金额"></el-table-column>
		<el-table-column prop="joinDate" label="订单时间"></el-table-column>
		<el-table-column prop="mName" label="市场人员"></el-table-column>
		<el-table-column label="购物车">
		<template scope="scope"><a :id="scope.row.buyId" v-on:click="detail" class="detail">详情</a></template>
		</el-table-column>
    </el-table>
}

12. ElementUI <el-tabs> 问题  {
	1~ tabs中设置@tab-click=“fn”， tab-pane 要设置onclick=“paneFn（）” 在js中methods中定义fn如何访问paneFn（）： 一定要使用tab.$el.onclick来访问
		1） // 匿名函数
		fn: function(tab, event) {
            (function(f) {
                f();
            })(tab.$el.onclick);
		}
		2） // 声明另外一个函数，并调用
		fn: function(tab, event) {
            function s(fn) {
                fn();
            }
            s(tab.$el.onclick);
		}
		原理：$el表示元素本身，因此可以调用元素的原生方法，例如$el.getAttribute('id')等等
	2~
}

13. 使用axios.post传递参数，需要JSON.stringigy才可以 {
	let data = JSON.stringify({
	userName: vm.phone,
	password: vm.password
});
}

14. JSX中{}内可以使用动态数据，即使在标签中属性值也可以。 注意“{link}”部分{
						renderContent(h, { node, data, store }) {
							let linkHtml = data.menuLinkUrl;
							let link = linkHtml.split('.')[0];
							if (node.level == 1 ) {
							return (
							<span>{ node.label }</span>
							);
                            } else if (node.level == 2) {
                                return (
                                <router-link to={ link }><span>{ node.label }</span></router-link>
                                )
                            }
						}
}

15. Vue 组件互相通信使用vm.$root.eventHub.$emit / $on, 如下： {
		// app.js
		new Vue({
			data: {
			eventHub: new Vue(),
			}
		}).$mount('#app')

		// login.vue 其他组件 methods中相关事件函数
			vm.$root.eventHub.$emit('fn');

		// bone.vue 主文件组件 created部分
			this.$root.eventHub.$on('fn', function () {some function}

		but 只能有一个主文件组件bone.vue，并且HTML只能有一个<div id="app"></div>

		but 兄弟组件之间通信传递的数据只存在于created中，在其他时候调用为undefined，目前不知成因

		but 父子组件之间建议不要用中央事件总线进行通信，直接props和$emit进行通信，否则总出现无关的子组件数据一直存在跟着提交的问题
}

16. Vue 点击按钮渲染一个新组件，可以在放在一个空ul中，使用:is属性实现： {
	// template
		<ul>
			<li>
			<product-table></product-table>
			</li>
			<li v-for="item in items" :is="item.component"></li>
			<el-row type="flex" justify="end"><el-button class="add-btn" type="text" @click="addTable('product-table')">添加一个新产品</el-button></el-row>
        </ul>
	// script
		import ProductTable from './Product-table.vue'

		export default {
			components: {'product-table': ProductTable},
			data() {
				return {
					items: []
				}
			},
			methods: {
                addTable(component)
                {
                    let vm = this;
                    vm.items.push({component});
                }
            }
}
}

17. Vue 子组件用父组件的数据，用props:[子组件绑定数据]：{
    		// Hd子组件template
			<span>{{userName}}</span>
			// Hd子组件script
        	props: ['userName'],
			// 父组件template
            <hd :user-name="name"></hd>
			// 父组件script
			data:{name: 'blablabla'}

    }

18. Vue 路由组件之间传数据，用组件通信似乎不好使，用sessionStorage：{
		// choose组件
        vm.bankerIds = new Array();
        for (let i = 0; i < vm.checkSelections.length; i++) {
            vm.bankerIds.push(vm.checkSelections[i].id);
        }
        sessionStorage.setItem('ids', vm.bankerIds);
        window.location.href = '/#/describe';
        // describe 组件
        let ids = sessionStorage.getItem('ids');
        console.log(ids);
}

19. Vue 子组件不允许双向绑定prop，如果需要，可设置prop的备份用来双向绑定 {
        // script
		props: ['quoteId', 'title', 'rate', 'productId', 'remarks'],
		data() {
			return {
				quoteObj: {},
				u_quoteId: this.quoteId,
				u_title: this.title,
				u_rate: this.rate,
				u_remarks: this.remarks,
				u_productId: this.productId
			}
        },
		// template
    	<input v-model="u_rate" />
        <input v-model="u_remarks" />
		这时更改u_rate的值则可以生效
}

20. vue-router带参数跳转： {
        // 当前页面
		vm.$router.push({name: 'detail', params: { 'id': id }}); // 注意，一定要有name，只用path不行~
		// 目标页面
        console.log(vm.$route.params.id);
}

21. render函数创建带有v-for的元素不能直接写v-for，应使用js原生map方法： {
        h('div', null,[
            h('p', null, '询价标题： ' + title),
//                            产品信息分行显示，使用render函数，规定不能直接写模板语法v-for，故使用原生js方法map代替
            h(
                'div',
                null,
                vm.msg.map(function (item) {
                    return h('div', null, item)
                })
            )
        ]),
}

22. login与主系统页面长的不一样时，建议使用嵌套路由：{
		外层为App.vue
		login与framework同为一级路由
		其他页面home、user等等为framework的子路由
        const routes = [
            {path: '/', redirect: '/login'},
            {path: '/login', name: 'login', component: Login},
            // vue提示当framework有默认子路由时，则不给framework设置name，而是调用默认子路由的name
            {path: '/framework', component: Framework, children: [
                {path: '', name: 'home', component: Home},
                {path: 'home', component: Home},
                {path: 'check', name: 'check', component: Check},
                {path: 'registered', name: 'registered', component: Registered},
                {path: 'init-enquiry', name: 'init-enquiry', component: Choose},
                {path: 'describe', name: 'describe', component: Describe},
                {path: 'enquiry-list', name: 'enquiry-list', component: EnquiryList},
                {path: 'detail', name: 'detail', component: Detail}
            ]},
        ];
}

23. webpack代理问题： {
		proxy: {
			// FOL代理，包含两个服务
			'/login-service': { // 不能代理到根目录，'/' or '//'都有问题
				target: 'http://192.168.7.28/login-service', // 把地址写到代理名称后为止，url也从代理名称前开始 let url = '/login-service/doLogin.apec';
				changeOrigin: true,
				pathRewrite: {
				'^/login-service': '' // 可写可不写
				}
			},
			'/BILLTOWMS-SERVICE': { // 有两个服务就写两个代理~
				target: 'http://192.168.7.28/BILLTOWMS-SERVICE',
				changeOrigin: true,
				pathRewrite: {
				'^/BILLTOWMS-SERVICE': ''
				}
			},

			// 中农e价代理
			'/enquiry': { // 所有接口在一个服务下面的话，可选服务中包含的路径作为代理路径
				target: 'http://192.168.7.24:20050', // 可不写到路径为止，let url = '/enquiry/manager/viewProduct';
				changeOrigin: true,
				pathRewrite: {
				'^/enquiry': 'http://192.168.7.24:20050'
				}
			}
		},
}

24. el-tree组件的loadNode方法需要lazy属性，否则就不加载子数据：{
			// html
			<el-tree node-key="path" :default-expanded-keys="['1']" :data="orgList" :props="props" :load="loadNode" lazy @node-click="retrieveStaffList" highlight-current>
			</el-tree>

			// js
			methods: {
				loadNode: function(node, resolve) {
					var vm = this;
					var url = '/STAFF-SERVICE/config/getOrg.apec';
					var param = {
						parentNo: node.data.deptNo
					};
						var callback = function (data) {
						if (data.data) {
						return resolve(data.data.secondList);
					} else {
						return resolve([]);
					}
					};
						if (node.level == 0) {
						return resolve(vm.orgList)
					} else {
						ajaxHelper.post(url, param, callback);
					}
				},
			｝
		}
}

25. html自定义属性的值可通过事件event.currentTarget.getAttribute('attr')获取
    ```
    event.currentTarget.setAttribute('style', 'pointer-events: initial; opacity: initial;');
    ```

26. axios 报错 cannot read 'protocol' of undefined 是指请求的参数不存在如ax.post(url, param, callback), url 不存在

27. safari 浏览器 new Date(String) 时，只支持'2018/03/27'的格式，chrome支持'2018-03-27'和'2018/03/27'，所以应在时间格式化函数中识别字符串并将'-'转为'/'，而且日期字符串需要写全，加日-01，否则苹果环境会不识别日期，变成invalid date

28. 箭头函数的this绑定到定义时的对象
    ```
    const drawCharts = (opts) => {
        const width = getApp().globalData.device.windowWidth;
        return new wxCharts({
            // componentInstance: this, // 箭头函数的this指向定义时的对象，即undefined，调用时不会被改变，call、apply、bind都不好使
            width,
            height: 300,
            dataLabel: true,

            ...opts
        })
    };
    ```

29. CSS 命名规范 -- BEM模式
    * .block 代表了更高级别的抽象或组件。
    * .block__element 代表.block的后代，用于形成一个完整的.block的整体。
    * .block--modifier代表.block的不同状态或不同版本。
    ```
    .block {}
    .block__element {}
    .block--modifier {}
    ```
    > 之所以使用两个连字符和下划线而不是一个，是为了让你自己的块可以用单个连字符来界定，如：
    ```
    .site-search {} /* 块 */
    .site-search__field {} /* 元素 */
    .site-search--full {} /* 修饰符 */
    ```

30. String.replace(reg, func(match, $1, $2, ..., offset, string))中func的参数
    ```
    @param {String} match, 匹配到的字串
    @param {reg$n} $1, $2, ... reg中的n个括号的引用，平铺起来
    @param {Number} offset, 匹配到的子字符串在原字符串中的偏移量 // 匹配多字符串情况再尝试
    @param {String} string, 原字符串
    ```
