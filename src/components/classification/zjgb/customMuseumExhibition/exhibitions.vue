<template>
	<!--展览展讯-->
	<div id="exhibition">
		<div class="swipeDiv">
			<mt-swipe  :auto="4000" :show-indicators="false">
			  <mt-swipe-item v-for='itme in list'>
			  	<img :src="hostUrl+itme.filePath" style="width: 100%;height: 100%;"/>
			  </mt-swipe-item>
			</mt-swipe>
		</div>
		<div class="exhibitList">
			<router-link to="/exhibitionClassification?type=jbcl&tittle=基本陈列">
				<div class="exhibitBtn">
					<div class="btnBox">
						基本陈列	
					</div>
					<div class="imgBox">
						<img :src="imgUrl+'/img/zlzx1_03.jpg'" alt="" />
					</div>
				</div>
			</router-link>
			<!--to="/exhibitionClassification?type=wltbz&tittle=未来特别展"-->
			<router-link to="/exhibitionClassification?type=wltbz&tittle=未来特别展">
				<div class="exhibitBtn">
					<div class="btnBox">
						未来特别展
					</div>
					<div class="imgBox">
						<img :src="imgUrl+'/img/zlzx3_03.jpg'" alt="" />
					</div>
				</div>
			</router-link>
			<router-link to="/exhibitionClassification?type=wqtbz&tittle=往期回顾展">
				<div class="exhibitBtn">
					<div class="btnBox">
						<!--往期特别展-->
						往期回顾展
					</div>
					<div class="imgBox">
						<img :src="imgUrl+'/img/zlzx2_03.jpg'" alt="" />
					</div>
				</div>
			</router-link>
		</div>
	</div>
</template>

<script>
import Api from '../../../../api.js'
	export default {
		data () {
	      return {
	     		imgUrl:Api.STATIC_SERVER_HOST,
	     		list:''
	     		
	      }	
	   	},
        methods: {
            fun (id){
                alert('建设中，敬请期待')
            }
        },
	   	 mounted(){
	    		var jsons = {
	    			'type':this.$route.query.type
	    		}
	    		Api.lunbo.list(jsons).then(res=>{
	    			this.hostUrl = res.data.url
	    			this.list = res.data.List
	    			console.log(this.list)
	    		},err=>{})
	    		

	    }
	}
</script>
