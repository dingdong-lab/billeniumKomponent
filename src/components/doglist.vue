<template>
	<div id='doglist' class='doglists'>
	  <div v-for='dog in dogs' class='dogselem'>
		 <div><img v-bind:src='dog.image'></div>
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
		   <li><div>{{dog.prohibiton}}</div></li>
		   <li><div>{{dog.advice}}</div></li>
		 </ul>
	  </div>
	</div>
</template>

<script>
	export default {
	data() {
		return {
			dogs: [
			{name: 'Dog niemiecki', 
			image: 'https://www.zooplus.pl/magazyn/wp-content/uploads/2021/04/dog-niemiecki-768x512.jpg',
			desc: 'Fajny pies niemiecki, ale jest agresywny, mocno gryzie ;/',
			prohibiton: 'Trzymać z dala od dzieci',
			advice: 'Dużo głaskać',
			descState: false
			},
			{name: 'Labrador', 
			image: 'https://zwierzaki.pl/wp-content/uploads/2021/08/labrador-retriever-1200x900.jpg',
			desc: 'Bardzo fajny i przyjemny piesek, nie można się przyczepić.',
			prohibiton: 'Ma alergię na karmę z wołowiną',
			advice: 'Dużo głaskać',
			descState: false
			}
		  ]
		}
	  },
	 methods: {
		showLimitedDesc(dog) {
			return dog.desc.substr(0, 50)+'...'
		},
		showFullDesc(dog) {
			return dog.desc
		},
		changeDescState(dog) {
			dog.descState = !dog.descState
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