<template>
  <div id="app">
    <h1>井字棋</h1>
    <div class="refresh" @click.prevent="refresh"><img src="./assets/images/refresh.png" /></div>
    <div class="jzq">

      <cell @fucell="bian(0,$event)" :n="n"  ref="cell1"></cell>
      <cell @fucell="bian(1,$event)" :n="n"  ref="cell2"></cell>
      <cell @fucell="bian(2,$event)" :n="n"  ref="cell3"></cell>
      <cell @fucell="bian(3,$event)" :n="n"  ref="cell4"></cell>
      <cell @fucell="bian(4,$event)" :n="n"  ref="cell5"></cell>
      <cell @fucell="bian(5,$event)" :n="n"  ref="cell6"></cell>
      <cell @fucell="bian(6,$event)" :n="n"  ref="cell7"></cell>
      <cell @fucell="bian(7,$event)" :n="n"  ref="cell8"></cell>
      <cell @fucell="bian(8,$event)" :n="n"  ref="cell9"></cell>




 


    </div>
<p class="res" >{{res==null?"胜负未分":"胜方为"+res}}</p>

  </div>
</template>

<script>
import cell from './components/cell'
export default {
  name: 'app',
  data () {
    return {
      n:0,
      map:[[null,null,null],[null,null,null],[null,null,null]],
      res:null
     
    }
  },
  methods:{
    bian:function(index,text){
      this.n++;
      this.map[Math.floor(index/3)][index%3]=text;
      this.jisuan();
   
    

    },
    jisuan:function(){
      let map=this.map;
      for(let i=0;i<2;i++){
        if( map[i][0]!==null && map[i][0]===map[i][1] && map[i][1]===map[i][2] ){
          this.res= map[i][0]
        }

      }
      for(let j=0;j<2;j++){
        if(map[0][j]!==null&&map[0][j]===map[1][j]&&map[1][j]===map[2][j]){
          this.res=map[0][j]
        }

      }
      if(map[0][0]!==null && map[0][0]===map[1][1]&&map[1][1]===map[2][2]){
          this.res=map[0][0]
      }
      if(map[2][0]!==null && map[2][0]===map[1][1]&& map[1][1]===map[0][2]){
          this.res=map[2][0]
      }     
      if(this.res!==null){
        alert("胜方为"+this.res);

      } 
     if(this.n==9){
       if(this.res!==null){
         return;
       }
        alert("胜负未分");

      } 

    },
    refresh:function(){
        this.n=0;
        this.map=[[null,null,null],[null,null,null],[null,null,null]];
        this.res=null;
        this.$refs.cell1.show=false;
        this.$refs.cell1.text="";     
        this.$refs.cell2.show=false;
        this.$refs.cell2.text=""; 
        this.$refs.cell3.show=false;
        this.$refs.cell3.text=""; 
        this.$refs.cell4.show=false;
        this.$refs.cell4.text=""; 
        this.$refs.cell5.show=false;
        this.$refs.cell5.text=""; 
        this.$refs.cell6.show=false;
        this.$refs.cell6.text=""; 
        this.$refs.cell7.show=false;
        this.$refs.cell7.text=""; 
        this.$refs.cell8.show=false;
        this.$refs.cell8.text=""; 
        this.$refs.cell9.show=false;
        this.$refs.cell9.text="";   
    }

  },
  components:{
    cell
  }
}
</script>

<style>
body, div, ol, ul, li, dl, dt, dd, h1, h2, h3, h4, h5, h6, p, form, fieldset, legend, input, button, figcaption, figure, textarea, img { margin: 0; padding: 0; border: 0; }
body{
  background:url(./assets/images/body-bg.jpg);
}
html,body,#app{
  height:100%;
}
#app{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

}
h1{
  font-size: 2rem;
  line-height: 2em;
  color: #fff;
      text-shadow: 0.2rem 0.2rem 0.2rem rgba(0,0,0,0.3);
}
.jzq{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  width: 13.2rem;

  background:url(./assets/images/jzq-bg.jpg);  
}

.res{
  font-size: 1rem;
  color: #fff;
  margin-top: 0.4rem;
  text-transform: uppercase;
}
.refresh{
  position: fixed;
  top: 1rem;
  right: 1rem;
  width: 2rem;
  float: right;
  cursor: pointer;
}
.refresh img{
  width: 2rem;
}
</style>
