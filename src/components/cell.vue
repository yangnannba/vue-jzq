<template>

    <div class="cell" @click="xiaqi">
        <template v-if="show">{{text}}</template>
        <template v-else></template>
    </div>


</template>

<script>
export default {
  name: 'cell',
  props:["n"],
  data () {
    return {
        show:false,
        text:''
     
    }
  },
  methods:{
      xiaqi:function(){
          if(this.text!==""){
              return;

          }
          this.show=true;
          this.text= this.n%2===0 ? "x" : "o" ;
          this.$emit("fucell",this.text);
      }
  }
}
</script>

<style>
.cell{
    width: 4rem;
    height:4rem;
    font-size: 4rem;
    text-align: center;
    line-height: 4rem;
    text-transform: uppercase;
    color: #fbd164;
    text-shadow: 0.2rem 0.2rem 0.2rem rgba(0,0,0,0.3);
    font-weight: bold;
    border:0.2rem solid #d0b56e;

}
</style>
