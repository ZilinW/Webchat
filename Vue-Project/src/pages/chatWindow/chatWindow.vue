<template>
	<div class='main'>
		<div class='title'>
			{{title}}
		</div>
		<div id='window'>
			<div id='textbox'>
				<div class='msg_line' v-for='(item, index) in chatArrays' :key="index">
					<span class='msg_standard' 
						  :class="{fl: item.id === 'a', fr: item.id === 'b'}"
					>
						用户:{{item.id}} 消息:{{item.value}}
					</span>
				</div>
			</div>
			<div>
				<div class='fl'>
					<input type='text' v-model='a_inputValue' placeholder='请输入' >
					<button @click="get_msg('a')">发送</button>
				</div>
				<div class='fr'>
					<input type='text' v-model='b_inputValue' placeholder='请输入' >
					<button @click="get_msg('b')">发送</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default{
  name: 'chatWindow',
  data() {
	  return{
		  title: 'hello Webchat',
		  msg: '请输入',
		  a_inputValue: '',
		  b_inputValue: '',
		  chatArrays: []
	  }
  },
  methods:{
	  get_msg: function(Id){
		  var Value;
		  if(Id === 'a')
		  	Value = this.a_inputValue
		  else
            Value = this.b_inputValue
		  var msg_obj = {
					id: Id,
			  		value: Value
				  };
		  this.chatArrays.push(msg_obj);
		  this.a_inputValue = this.b_inputValue = '';
		  console.log(chatArrays);
	  }
  }
}
</script>

<style>
.main{
	width: 100%;
	height: 800px;
	background-color:gray;
}
.title{
	font-size: 20px;
	font-family: "仿宋";
	text-align: center;
}
.msg_line{
	width: 100%;
	display: inline-block;
}
.msg_standard{
	line-height: 20px;
	font-size: 20px;
	background-color: aqua;
}
.fl{
	float: left;
}
.fr{
	float: right;
}

#window{
	width: 800px;
	height: 750px;
	background-color: red;
	margin: 10px auto;
}
#textbox{
	width:800px;
	height:500px;
	overflow: hidden;
	background-color: wheat;
}
</style>
