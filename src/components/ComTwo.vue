<template>
	<div>
    <!-- 原生事件绑定到组件，没有label时父组件直接用.native修饰符即可获取到，但以下这种重构input的情况下父组件的.native静默失效(无报错但onFocus处理函数不会被调用) -->
    
		<!-- <label>
			{{ label }}
			<input :="$attrs" :value="value" @input="$emit('input', $event.target.value)" />
		</label> -->

    <!-- 因此组件内提供了一个$listeners 属性,它是一个对象，里面包含了作用在这个组件上的所有监听器 -->
    <label>
			{{ label }}
			<input :value="value" v-bind="$attrs" v-on="inputListeners" />
		</label>
	</div>
</template>

<script>
export default {
	inheritAttrs: false,
	props: ['label', 'value'],
	computed: {
		inputListeners: function () {
			var vm = this;
			// `Object.assign` 将所有的对象合并为一个新对象
			return Object.assign(
				{},
				// 我们从父级添加所有的监听器
				this.$listeners,
				// 然后我们添加自定义监听器，
				// 或覆写一些监听器的行为
				{
					// 这里确保组件配合 `v-model` 的工作
					input: function (event) {
						vm.$emit('input', event.target.value);
					},
          focus:function(e){
            vm.$emit('focus','focus触发')
          }
				}
			);
		},
	},
  mounted () {
    console.log('$attrs---',this.$attrs);
    console.log('$listeners---',this.$listeners);
  },
};
</script>

<style lang="scss" scoped></style>
