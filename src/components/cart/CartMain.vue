<template>
		<main class="cart_box">
		    <div class="cart_content clearfix"  v-for="(item,i) in cartDatas" :key="i">
		        <div class="cart_shop clearfix">
		            <div class="shop_info clearfix">
						<input type="checkbox" :checked="item.state" @click="stateToggle(item.product_id)"/>
		                <img src="../../assets/images/buy-logo.png" alt="" class="shop_icon">
                  <span class="shop_name">{{item.shop_name}}</span>
		            </div>
		            <div class="cart_free clearfix">
		                <span class="free_tip">优惠券></span>
		            </div>
		        </div>
		        <div class="cart_item">
		            <div class="cart_detial_box clearfix">
		                <a href="#" class="cart_product_link">
                      <img v-lazy="item.product_img_url" alt="">
		                </a>
		                <div class="item_names">
		                    <a href="#">
                          <span>{{item.product_name}}</span>
		                    </a>
		                </div>
		                <div class="cart_weight">
		                    <i class="my_weigth">重量:0.45kg</i>
		                    <span class="my_color">颜色:AT800/16</span>
		                </div>
		                <div class="cart_product_sell">
		                    <span class="product_money">￥<strong class="real_money">{{item.product_price}}</strong>.00</span>
		                    <div class="cart_add clearfix">
		                        <span class="my_add" @click="addNum(item.product_id)">+</span>
		                        <input type="tel" class="my_count" v-model="item.num">
		                        <span class="my_jian"  @click="decreaseNum(item.product_id)">-</span>
		                    </div>
		                </div>
		                <div class="cart_del clearfix" @click="delPop(item.product_id)">
		                    <div class="del_top" >
		                    </div>
		                    <div class="del_bottom">
		                    </div>
		                </div>
		            </div>
		        </div>

		    </div>

		    <div class="pop" v-show="popStatus">
		    <div class="pop_box">
		        <div class="del_info">
		            确定要删除该商品吗？
		        </div>
		        <div class="del_cancel" @click="delCancel">
		            取消
		        </div>
		        <div class="del_ok" @click="delOk">
		            确定
		        </div>
		    </div>
		</div>

		</main>
</template>
<script>
	import {mapGetters, mapActions} from 'vuex'
	export default{
		data(){
			return{
				popStatus: false, //弹层隐藏   true显示
        delId:-1
			}
		},
		//计算属性
		computed:{
		    ...mapGetters(['cartDatas']),
    },
		methods: {
		    ...mapActions(['addNum','decreaseNum','stateToggle','deleteGoods']),
        delPop(id){
		        this.popStatus=true;
		        this.delId=id;
        },
        delCancel(){
            this.popStatus=false;
        },
        delOk(){
            this.popStatus=false;
            this.deleteGoods(this.delId);
        }
    }
	}
</script>
