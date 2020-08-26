<template>
  <div id="app">
  

      <p>Male</p>

{{nameCatsMaleOwner}}


      

      <p>Female</p>
{{nameCatsFemaleOwner}}

    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          
        </b-col>
      </b-row>
</b-container>

   
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {
   

  },
  data(){
    return {
      maleOwner:[],
      femaleOwner:[],
      nameCatsMaleOwner:[],
      nameCatsFemaleOwner:[],
      index: 0
    }
  },
  methods: {
    next(){
      this.index++
    }
  },
  
  mounted: function(){
    fetch('http://agl-developer-test.azurewebsites.net/people.json',{
      method:'get'
    })
    .then((response) => {
      return response.json()
    })
    .then((jsonData) => {
  

       for(var i =  0; i<jsonData.length;i++){
          if(jsonData[i].gender==='Male')
          this.maleOwner.push(jsonData[i].pets)
          else
          this.femaleOwner.push(jsonData[i].pets)

       }

//console.log(this.maleOwner[0][0].type)



          for (var pet of this.maleOwner) {
            console.log(pet)
            //nameCatsMaleOwner
          }
/*
       for( i =  0; i<this.maleOwner.length;i++){

         var i2 = 0


         while(this.maleOwner[i] !== null && this.maleOwner[i].length>i2 ){

         if(this.maleOwner[i][i2].type === 'Cat')
         this.nameCatsMaleOwner.push(this.maleOwner[i][i2].name)

         i2++
       }

       }

       for( i =  0; i<this.femaleOwner.length;i++){

          i2 = 0


         while(this.femaleOwner[i] !== null && this.femaleOwner[i].length>i2 ){

         if(this.femaleOwner[i][i2].type === 'Cat')
         this.nameCatsFemaleOwner.push(this.femaleOwner[i][i2].name)

         i2++
       }

       }
*/

    })
  },
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


