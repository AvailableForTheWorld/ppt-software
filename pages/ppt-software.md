- # 项目结构分析
- # 配置文件
	- ## vue.config.js
	  —— Vue cli 中 webpack的配置
		- ### 预知识：
			- Webpack
				- 用于项目打包，可以减少项目大小，并且可以加载一些预加载器即原本js html无法加载的东西，例如：typescript，sass等，减少io调用提高性能。
		- ### 模块化
		  module.exports 对外暴露内容
			- publicPath：部署应用包时的基本 URL
			- css  ： 配置css对应的选项
				- loaderOptions：webpack中的加载器
					- Sass
						- prependData 引入全局css
			- configWebpack：用于webpack的方式配置
				- 对象形式：直接将对象merge到最终配置中
				- 函数形式：将解析配置传入，直接修改解析配置的属性
		- ### tsconfig.json
			- compilerOptions
				- module : commonjs 规范
				- commonjs：require 加载模块 exports、module.exports导出
				- Target:  tsc--> typescript compiler  编译的目标
				- Esnext 当前发布版本的下一个版本 最新的js特性
				- Strict 采用严格模式
				- Jsx 使用jsx后缀文件编写组件
				- importHelpers 通过tslib引入helper函数，文件必须是模块
				- moduleResolution 模块解析策略 一般使用node.js
				- skipLibCheck 忽略所有的声明文件（*.d.ts）的类型检查
				- esModuleInterop 模块打包后的转译方式是否采用esModule
				- allowSyntheticDefaultImports 判断初始化模块化是怎样的模块化
				- suppressImplicitAnyIndexErrors 防noImplicitAny报错中由于index的对象缺少指定标签而报错的问题发生
				- sourceMap 找到信息定位至项目打包前的位置
				- baseUrl 指定基本目录以解决不相关模块名字
				- Types 指定不在源文件中引用而要包含的类型包名称
				- Paths 定义路径标识符
				- Lib 指定一组描述目标库/执行期函式库的绑定库声明文件
			- Include
				- 指定tsconfig配置项所要包含的文件/文件夹名
			- Exclude
				- 指定tsconfig配置项所要排除的文件/文件夹名
		- ### Babel.config.js
			- 用于将ex6及以上版本的js语法转换成老版本语法以兼容浏览器
			- Presets 导入的预设内容名
			- Plugin 导入的预设插件
- **代码 src目录**
	- Assets 静态资源
		- Fonts 字体文件夹
		- Styles 样式文件夹
	- Components 组件
		- 拆分成不同的一个一个的功能小模块
	- Configs
		- ppt的一些配置方法
	- Hooks
		- 功能型函数
	- Mocks
		- 组件的功能化配置
	- Plugins
		- 插件：提供组件的必要功能
	- Store
		- 数据状态管理
	- types
		- ppt中的一些数据的typescript类型的定义
	- utils
		- 交互操作所需要的工具文件夹
	- views
		- 视图层文件夹
		- Editor
			- EditorHeader
				- Dropdown —— ant-design-vue
				  使用方法：将插槽中包裹我们要渲染的元素，第一个元素是标题，第二个元素是下拉菜单
				  源码分析：
				  1.引入的一个vue的组件实例作为它的根元素
				  2.挂载一些事件出发（其中包括slots）
				- Menu ——ant-design-vue
					- slots：Menu-item
					- 绑定exportJSON以及exportPPTX事件——来自useExport
					- exportJSON：
						- 通过将数据传入Blob构造函数构造，这个是将数据转换为一种文件格式的方法
						- 后期增加通过JSON格式导入的功能
						  background-color:: #978626
					- Icon-park
	- App.vue
		- VUE中的根组件
		- 三个视图组件
			- 1.Screen
			  		  通过screening这个条件判断是否生效否则执行后面的组件
			- 2.Editor
			  		  通过isPC判断这个条件是否生效否则执行后面的组件
			- 3.Mobile
	- components.d.ts
		- 组件文件夹中的头文件
	- global.d.ts
		- 全局的头文件
	- shims-vue.d.ts
		- 为 typescript 做的适配定义文件，将里面的components组件定义
	- main.ts
		- 初始化项目的根文件
			- 引入vue createApp
			- 引入pinia状态管理 createPinia 并use
			  background-color:: #978626
			- 引入根组件 App
			  background-color:: #793e3e
			- 引入各种样式 css，scss
			- 引入插件plugins
			  background-color:: #978626
			- 引入ant-design-vue，并将其绑定到vue对象中
			- 挂在到id为app的div中