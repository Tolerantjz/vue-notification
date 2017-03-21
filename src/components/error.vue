<template>
	<transition-group name = "slide">
	<div class="parent"  key = "i" :class="{empty:isEmpty}">
		<div class="bro"  ref = "bro">
			<img src="../assets/Error.png" alt="sorry to see this please wait" />
			<div class="words">
				<span class="close" @click = "removeElement">X</span>
				<p class="titile">{{title}}</p>
				<p class="content">{{content}}</p>
			</div>
		</div>			
	</div>
	</transition-group>
</template>
<script>
	export default{
		name : "wrong",
		data(){
			return{
				isEmpty:false
			}
		},
		props : {
			title : String,
			content : String
		},
		methods:{
			removeElement(){
				console.log('remove this element')
				const self = this
				this.isEmpty = true
				setTimeout(function(){
//					alert('be going to remove')
					self.$emit('remove')
				},100)
			}
		},
		mounted(){
			console.log(window.getComputedStyle(this.$refs.bro).width)
			const self = this
			setTimeout(function(){
				if(self.isEmpty){
					return false
				}else{
					self.removeElement()				
				}
//				alert('i would be removed')
			},3000)
		}
	}
</script>
<style>
.parent{border: 1px solid black;position: relative;width: 25%;margin-bottom: 10px;border-radius: 5px;left: 105%;animation: move .5s ease forwards;background-color: white;}
@keyframes move{
	from{left: 105%;}
	to{left: 75%;}
}
.parent.empty{left:75%;animation: emptyHeight .5s linear forwards;}
@keyframes emptyHeight{
	100%{height: 100%;opacity: .5;}
	50%{opacity: .5;}
	0%{height: 0px;opacity: 0;}
}
img{width: 20%;position: absolute;top: 10px;}
.words{overflow: hidden;}
.words>span:hover{cursor: pointer;}
.close{float: right;margin: 5px;}
.titile,.content{margin-left: 46px;}
</style>