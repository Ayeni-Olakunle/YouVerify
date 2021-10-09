<template>
  <div id="app">
    <b-container class="bv-example-row">
      <h1 style="text-align: center;">You Verify Test</h1>
    <b-row>
      <b-col cols="12" class="general">
          <h3 class="TName">1. Is Unique</h3>
          <div>
            <b-form-input v-model="checkInput" placeholder="Enter your name" class="inputNow"></b-form-input><br>
            <b-button variant="primary" class="butin" @click="checkingBn">Check</b-button>
            <p class="valu"><span>Value:</span><span>{{ bool1 }}</span></p>
          </div>
      </b-col>
      <b-col cols="12" class="general">
        <h3 class="TName">2. Check Permutation</h3>
          <div>
            <b-form-input v-model="permutate" placeholder="Enter your name" class="inputNow"></b-form-input><br>
            <b-button variant="primary" class="butin" @click="permu">Check</b-button>
            <p class="valu"><span>Value:</span><span>{{ bool2 }}</span></p>
          </div>
      </b-col>
      <b-col cols="12" class="general">
        <h3 class="TName">3. URLify</h3>
          <div>
            <b-form-input v-model="replaceMe" placeholder="Enter your name" class="inputNow"></b-form-input><br>
            <b-button variant="primary" class="butin" @click="replaceWhite">Check</b-button><br><br>
            <p class="valu"><span>Value:</span><span>{{ bool3 }}</span></p>
          </div>
      </b-col>
      <b-col cols="12" class="general">
        <h3 class="TName">4. Palindrome  Permutation</h3>
          <div>
            <b-form-input v-model="checkReve" placeholder="Enter your name" class="inputNow"></b-form-input><br>
            <b-button variant="primary" class="butin" @click="rever">Check</b-button>
            <div class="mt-2 valu">Value: {{ bool4 }}</div>
          </div>
      </b-col>
      <b-col cols="12" class="general">
        <h3 class="TName">5. One Away</h3>
          <div>
            <b-form-input v-model="editFor" placeholder="Enter your name" class="inputNow"></b-form-input><br>
            <b-button variant="primary" class="butin" @click="editor">Check</b-button>
            <b-button variant="primary" class="butin" style="margin-left: 10px;">Edit</b-button><br><br>
            <div class="mt-2 valu">Value: {{ bool5 }}</div>
          </div>
      </b-col>
      <b-col cols="12" class="general">
        <h3 class="TName">6. String Compression</h3>
          <div>
            <b-form-input v-model="occur" placeholder="Enter your name" class="inputNow"></b-form-input><br>
            <b-button variant="primary" class="butin" @click="apper">Check</b-button><br><br>
            <p class="valu"><span>Value:</span><span id="derg">{{ bool6 }}</span></p>
          </div>
      </b-col>
      
    </b-row>
  </b-container>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      checkInput:"",
      bool1:"",
      checkReve: "",
      bool4:"",
      replaceMe: "",
      bool3:"",
      permutate:"",
      bool2:"",
      occur:"",
      bool6:"",
      editFor:"",
      bool5: ""
    }
  },
  methods:{
    checkingBn(){
      function unique_char(str1)
      {
      let str=str1;
      let uniql="";
      for (let x=0;x < str.length;x++)
      {

      if(uniql.indexOf(str.charAt(x))==-1)
        {
        uniql += str[x];  
        
        }
        }
        return uniql;  
      }  
      let eert = unique_char(this.checkInput)
      this.bool1 = eert
    },
    rever(){
        let ORs = this.checkReve
        let resd = this.checkReve.split('').reverse().join('')
        if (ORs == resd) {
          this.bool4 = true
        }
        else{
          this.bool4 = false
        }
    },
    replaceWhite(){
      let Oret = this.replaceMe
      this.bool3 = Oret.replace(/\s/g, '%20')
    },
    permu(){
      function getPermutations(string) {
        let results = [];

        if (string.length === 1) 
        {
          results.push(string);
          return results;
        }

        for (let i = 0; i < string.length; i++) 
        {
          let firstChar = string[i];
          let otherChar = string.substring(0, i) + string.substring(i + 1);
          let otherPermutations = getPermutations(otherChar);
          
          for (let j = 0; j < otherPermutations.length; j++) {
            results.push(firstChar + otherPermutations[j]);
          }
        }
        return results;
      }
      let permutation = getPermutations(this.permutate).filter((el, idx, self) => (self.indexOf(el) === idx));
      this.bool2 = "Total permutation: "+permutation.length
    },

    apper(){
      function printans( ans ){
        for( let [ key ,value] of ans){
          console.log(`${key}  occurs  ${value} times` );
          document.getElementById("derg").innerHTML+= ` ${key}  occurs  ${value} times <br>`
        }
      
      }
      
      function count( str , outp_map )
      {
        for( let i = 0 ;i < str.length ;i++)
        {
      
          let k = outp_map.get(str[i]);
          outp_map.set(str[i], k+1) ;
              
          
        }
        printans(outp_map);
      }
      
      function count_occurs( test , callback )
      {
        if( test.length === 0 )
        {
          console.log(" empty string ");
          return ;
        }
        else
        {
          let ans = new Map();
          for( let i = 0 ;i < test.length;i++)
          {
            ans.set(test[i], 0);
          }
          callback( test ,ans);
          
        }
      }
      let test =  this.occur;
      count_occurs( test ,count);
    },
    editor(){
      let desd = this.editFor
      this.bool5 = desd
    },
    Reeditor(){
      let desd = this.editFor
      let ret = this.bool5 = desd
      desd.value = ret.textContent
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.general{
  background-color: #e6e6e6;
  margin: 50px 0px;
  border-radius: 5px;
  padding: 10px;
}
.TName{
  text-align: left;
}
.inputNow{
  width: 50% !important;
  height: 50px !important;
  font-size: 20px !important;
  margin-top: 30px !important;
  margin-bottom: 20px !important;
}

.butin{
  font-size: 20px !important;
}
.valu{
  font-size: 25px !important;
  margin-top: 20px !important
}
</style>
