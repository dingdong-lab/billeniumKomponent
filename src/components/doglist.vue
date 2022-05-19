<template>
	<div id='doglist' class='doglists'>
	<div v-if='error'>Cos poszlo nie tak</div>
	  <div v-for='dog in dogs' :key="dogs.id" class='dogselem'>
		 <div><img src='https://www.zooplus.pl/magazyn/wp-content/uploads/2021/04/dog-niemiecki-768x512.jpg'></div>
		 <ul class='doginfo'>
		   <li><div>{{dog.name}}</div></li>
		   <li><div v-if='!dog.descState'>
			 {{showLimitedDesc(dog)}}
			 <button v-on:click='changeDescState(dog)'>Więcej</button>
		   </div>
		   <div v-else>
			 {{showFullDesc(dog)}}
			 <button v-on:click='changeDescState(dog)'>Mniej</button>
		   </div></li>
		   <li><div>{{dog.username}}</div></li>
		   <li><div>{{dog.email}}</div></li>
		 </ul>
	  </div>
	  <button v-on:click='loadData()'>Zaladuj</button>
	</div>
</template>

<script>
	import axios from 'axios';
	
	export default {
	data() {
		return {
			dogs: [],
			error: false
		}
	  },
	 methods: {
		showLimitedDesc(dog) {
			var info = dog.address['street']+' '+dog.address['suite']+' '+dog.address['city']+' '+dog.address['zipcode'];
			return info.substr(0, 50)+'...';
		},
		showFullDesc(dog) {
			var info = dog.address['street']+' '+dog.address['suite']+' '+dog.address['city']+' '+dog.address['zipcode'];
			return info;
		},
		changeDescState(dog) {
			dog.descState = !dog.descState;
		},
		async loadData() {
			let temp = null;
			axios.get("https://jsonplaceholder.typicode.com/users/")
			.then(result => { 
				this.dogs = result.data;
			})
			.catch(error => {
				this.error = true;
				alert(error);
			});
		}
	  }
	}
</script>

<style>
	.doglists {
	  width: 90%;
	  vertical-align: center;
	  background-color: WhiteSmoke;
	  border: 5px solid gray;
	}

	.dogselem > div {
	  width: 30%;
	  display: inline-block;
	}

	.dogselem img {
	  width: 90%;
	  margin: 5%;
	  height: auto;
	}

	.dogselem > ul {
	  width: 60%;
	  background-color: silver;
	  display: inline-block;
	  padding: 2% 5px;
	}

	.doginfo {
	  list-style: none;
	}

	.doginfo li {
	  margin-bottom: 5px;
	}

	.doginfo div {
	  border: 2px solid green;
	  border-radius: 5px;
	  padding: 5px 5px;
	}.doglists {
	  width: 90%;
	  vertical-align: center;
	  background-color: WhiteSmoke;
	  border: 5px solid gray;
	}

	.dogselem > div {
	  width: 30%;
	  display: inline-block;
	}

	.dogselem img {
	  width: 90%;
	  margin: 5%;
	  height: auto;
	}

	.dogselem > ul {
	  width: 60%;
	  background-color: silver;
	  display: inline-block;
	  padding: 2% 5px;
	}

	.doginfo {
	  list-style: none;
	}

	.doginfo li {
	  margin-bottom: 5px;
	}

	.doginfo div {
	  border: 2px solid green;
	  border-radius: 5px;
	  padding: 5px 5px;
	}
</style>