<template>
	<div class="cart_fo">
		<footer class="cart_footer">
			<div class="all_check_box">
				<input type="checkbox" :checked="checkAll" @change="checkAllToggle">
		        <span>全选</span>
			</div>
		    <div class="count_money_box">
		        <div class="heji">
		            <strong>合计:</strong>
		            <strong>￥</strong>
		            <strong>{{figureOut}}</strong>
		        </div>
		        <div class="total_money clearfix">
		            <span>总额:</span>
		            <i>￥</i>
		            <span></span>
		            <span>立减:</span>
		            <i>￥</i>
		            <span>0.00</span>
		        </div>>
		            <a href="#" class="go_pay">
		                <span>去计算(1)</span>
		            </a>
		    </div>
		</footer>
	</div>
</template>
<script>
	import {mapState,mapActions,mapGetters} from 'vuex'
	export default {
    data(){
      return {

      }
    },
    methods :{
     ...mapActions(['checkAllToggle'])
    },
    computed :{
        ...mapState(['checkAll']),
        ...mapGetters(['figureOut'])
    }
	}
</script>
<style>
	.cart_fo .cart_footer .all_check_box span{
		margin-left:0;
	}
</style>
