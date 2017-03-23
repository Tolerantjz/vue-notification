<template>
  <div id="app">
  	<ul ref = "tit">
  		<li v-for = "(v,index) in list" 
  				@click = "handleClick(null,index)"
  				ref = "content[index]">{{v.msg}}</li>
  	</ul>
  	<div>
  		<ul v-show = "ready">
  			<li v-for = "(item,index) in infoItems" 
  					v-model = "infoElement"
  				  is = "info" 
  					title = "Info" 
  					content = "I am info"
  					v-on:remove = "infoItems.splice(index,1)"></li>
				<li v-for = "(item,index) in errorItems"
						v-model = "errorElement"
					  is = "wrong" 
						title = "Error" 
						content = "I am error"
						v-on:remove = "errorItems.splice(index,1)"></li>
				<li v-for = "(item,index) in successItems" 
						v-model = "successElement"
					  is = "success" 
						title = "Success" 
						content = "I am success"
						v-on:remove = "successItems.splice(index,1)"></li>
				<li v-for = "(item,index) in warnItems" 
						v-model = "warnElement"
					  is = "warn" 
						title = "Warn" 
						content = "I am warn"
						v-on:remove = "warnItems.splice(index,1)"></li>
  		</ul>
  	</div>
  </div>
</template>

<script>
const list = [{msg:'Info'},{msg:'Error'},{msg:'success'},{msg:'warn'}]
const errorItems = [{}]
const successItems = [{}]
const infoItems = [{}]
const warnItems = [{}]
import wrong from './components/error.vue'
import info from './components/info.vue'
import success from './components/success.vue'
import warn from './components/warn.vue'
export default {
  name: 'app',
  components:{
  	wrong,
  	info,
  	success,
  	warn
  },
  data () {
    return {
     	list,
     	infoItems,
     	errorItems,
     	successItems,
     	warnItems,
     	infoElement:'',
     	successElement:'',
     	errorElement:'',
     	warnElement:'',
     	ready:false
    }
  },
  methods:{
  	handleClick(e,index){
  		this.ready = true
  		if(index === 0){
  			console.log('would be created an infoElement:',index)
				infoItems.push(this.index)
  		}else if(index === 1){
  			console.log('would be created an errorElement:',index)
				errorItems.push(this.index)
  		}else if(index === 2){
  			console.log('would be created a successElement:',index)
				successItems.push(this.index)
  		}else if(index === 3){
  			console.log('would be created a warnElement:',index)
				warnItems.push(this.index)
  		}
  	}
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

ul {
  list-style-type: none;
  padding: 0;
  height: 20px;
}

li {
	display: inline-block;
  float: left;
  margin: 0 5px;
  padding: 2px 5px;
  border-radius: 4px;
  border: 1px solid black;
}
li:hover{transition: all 0.5s;color:darkturquoise;border: 1px solid darkturquoise;cursor: pointer;}
a {
  color: #42b983;	
}
</style>
