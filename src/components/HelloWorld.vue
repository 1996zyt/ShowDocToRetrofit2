<template>
  <div class="hello">
    <span>请输入ShowDoc接口文档:</span>
    <br>
    <br>
    <textarea ref="et_sd" cols="160" rows="12" v-model="sd_text" placeholder=""></textarea>
    <br>
    <br>

    <button ref="bt_sd_to_retrofit" v-on:click="sd_to_retrofit()">代码转化</button>
    <br>
    <br>

    <span>转成Retrofit接口代码:</span>
    <br>
    <br>
    <textarea ref="et_retrofit" cols="160" rows="12"  v-model="retrofit_text" placeholder=""></textarea>
    <br>
    <br>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      message:'123',
      sd_text:'',
      retrofit_text:''
    }
  },

  methods:{
    sd_to_retrofit(){
      let sd_text = '';
      sd_text = this.sd_text;

      let snsArr;
      snsArr=sd_text.split(/[(\r\n)\r\n]+/);

      for (let i = 0; i< snsArr.length; i++){
        console.log(snsArr[i]);
      }

      if (snsArr.length == 11){
        let a = snsArr[8].trim().split(/\s+/);
        console.log(a);
        let b = snsArr[9].trim().split(/\s+/);
        console.log(b);
        let c = snsArr[10].trim().split(/\s+/);
        console.log(c);

        this.retrofit_text = "    /** \n " +
                "     * "+snsArr[1]+" \n " +
                "     * "+snsArr[8]+" \n " +
                "     * "+snsArr[9]+" \n " +
                "     * "+snsArr[10]+" \n " +
                "     */ \n " +
                "    @FormUrlEncoded \n "+
                "    @"+"POST"+"(\""+snsArr[3]+"\") \n " +
                "    Observable<BaseResponse<Bean>> "+snsArr[3].replace("/","")+"(@Field(\""+a[0]+"\") "+(a[2].includes('s')?"String":a[2])+" "+a[0]+", \n" +
                "                                                          @Field(\""+b[0]+"\") "+(b[2].includes('s')?"String":b[2])+" "+b[0]+", \n" +
                "                                                          @Field(\""+c[0]+"\") "+(c[2].includes('s')?"String":c[2])+" "+c[0]+");";
      }else if (snsArr.length == 9){
        let a = snsArr[8].trim().split(/\s+/);
        console.log(a);

        this.retrofit_text = "    /** \n " +
                "     * "+snsArr[1]+" \n " +
                "     * "+snsArr[8]+" \n " +
                "     */ \n " +
                "    @FormUrlEncoded \n "+
                "    @"+"POST"+"(\""+snsArr[3]+"\") \n " +
                "    Observable<BaseResponse<Bean>> "+snsArr[3].replace("/","")+"(@Field(\""+a[0]+"\") "+(a[2].includes('s')?"String":a[2])+" "+a[0]+");";

      }else if (snsArr.length == 10){
        let a = snsArr[8].trim().split(/\s+/);
        console.log(a);
        let b = snsArr[9].trim().split(/\s+/);
        console.log(b);

        this.retrofit_text = "    /** \n " +
                "     * "+snsArr[1]+" \n " +
                "     * "+snsArr[8]+" \n " +
                "     * "+snsArr[9]+" \n " +
                "     */ \n " +
                "    @FormUrlEncoded \n "+
                "    @"+"POST"+"(\""+snsArr[3]+"\") \n " +
                "    Observable<BaseResponse<Bean>> "+snsArr[3].replace("/","")+"(@Field(\""+a[0]+"\") "+(a[2].includes('s')?"String":a[2])+" "+a[0]+", \n" +
                "                                                          @Field(\""+b[0]+"\") "+(b[2].includes('s')?"String":b[2])+" "+b[0]+");";

      }else if (snsArr.length == 12){
        let a = snsArr[8].trim().split(/\s+/);
        console.log(a);
        let b = snsArr[9].trim().split(/\s+/);
        console.log(b);
        let c = snsArr[10].trim().split(/\s+/);
        console.log(c);
        let d = snsArr[11].trim().split(/\s+/);
        console.log(d);

        this.retrofit_text = "    /** \n " +
                "     * "+snsArr[1]+" \n " +
                "     * "+snsArr[8]+" \n " +
                "     * "+snsArr[9]+" \n " +
                "     * "+snsArr[10]+" \n " +
                "     * "+snsArr[11]+" \n " +
                "     */ \n " +
                "    @FormUrlEncoded \n "+
                "    @"+"POST"+"(\""+snsArr[3]+"\") \n " +
                "    Observable<BaseResponse<Bean>> "+snsArr[3].replace("/","")+"(@Field(\""+a[0]+"\") "+(a[2].includes('s')?"String":a[2])+" "+a[0]+", \n" +
                "                                                          @Field(\""+b[0]+"\") "+(b[2].includes('s')?"String":b[2])+" "+b[0]+", \n" +
                "                                                          @Field(\""+c[0]+"\") "+(c[2].includes('s')?"String":c[2])+" "+c[0]+", \n" +
                "                                                          @Field(\""+d[0]+"\") "+(d[2].includes('s')?"String":d[2])+" "+d[0]+");";



      } else {

        this.retrofit_text = "    /** \n " +
                "     * "+snsArr[1]+" \n " +
                "     */ \n " +
                "    @FormUrlEncoded \n "+
                "    @"+"POST"+"(\""+snsArr[3]+"\") \n " +
                "    Observable<BaseResponse<Bean>> "+snsArr[3].replace("/","")+"();";

      }


      console.log(sd_text);
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
