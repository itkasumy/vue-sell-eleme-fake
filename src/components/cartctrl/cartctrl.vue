<template>
	<div class="cartctrl">
		<transition name="move">
			<div class="cart-decrease icon-remove_circle_outline" v-show="food.count > 0" @click.stop.prevent="decreaseCart"></div>
		</transition>
		<div class="cart-count" v-show="food.count > 0">{{food.count}}</div>
		<div class="cart-add icon-add_circle" @click.stop.prevent="addCart"></div>
	</div>
	</div>
</template>
	
<script>
	import Vue from 'vue'

	export default {
		props: {
			food: {
				type: Object
			}
		},
		methods: {
			addCart (event) {
				!this.food.count ? Vue.set(this.food, 'count', 1) : this.food.count++
				this.$emit('increament', event.target)
			},
			decreaseCart () {
				if (this.food.count) {
					this.food.count--
				}
			}
		}
	}
</script>

<style scoped lang='stylus' rel='stylesheet/stylus'>
	.cartctrl
		font-size 0
		.cart-decrease
			display inline-block
			padding 6px
			font-size 24px
			line-height 24px
			color rgb(0, 160, 220)
			transition all .4s linear
			&.move-enter-active, &.move-leave-active
				opacity 1
				transform translate3d(0, 0, 0) rotate(0)
			&.move-enter, &.move-leave-to
				opacity 0
				transform translate3d(24px, 0, 0) rotate(180deg)
		.cart-count
			display inline-block
			vertical-align top
			width 12px
			padding-top 6px
			line-height 24px
			text-align center
			font-size 10px
			color rgb(147, 153, 159)
		.cart-add
			display inline-block
			padding 6px
			font-size 24px
			line-height 24px
			color rgb(0, 160, 220)
</style>