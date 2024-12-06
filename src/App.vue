
<template>  
  <div>
    <!-- <input v-model="input_text1">
    <button @click="mycom()">点击计算</button> -->
    <button @click="exportPDF">导出PDF</button>
    <button @click="mycompu">计算结果</button>
    <div ref="pdfContent">
      <table class="table" border="2">
        <tr>
          <th colspan="7" class="table-title-1">项目前评估打分表</th>
          <th style="display: none;">项目前评估打分表</th>
          <th style="display: none;">项目前评估打分表</th>
          <th style="display: none;">项目前评估打分表</th>
          <th style="display: none;">项目前评估打分表</th>
          <th style="display: none;">项目前评估打分表</th>
          <th style="display: none;">项目前评估打分表</th>
        </tr>
        <tr>
          <th colspan="3" class="table-title-2">评估细则</th>
          <th style="display: none;">评估细则</th>
          <th style="display: none;">评估细则</th>
          <th colspan="4" class="table-title-3">前评估</th>
          <th style="display: none;">前评估</th>
          <th style="display: none;">前评估</th>
          <th style="display: none;">前评估</th>
        </tr>
        <tr>
          <th class="table-title-2" style="width: 100px;">评估维度</th>
          <th class="table-title-2" style="width: 300px;">评估内容</th>
          <th class="table-title-2" style="width: 300px;">分值区间</th>
          <th class="table-title-3">计划达到值<br>(请按要求填写)</th>
          <th class="table-title-3" style="width: 300px;">填写内容说明</th>
          <th class="table-title-4" style="width: 50px;">单项得分</th>
          <th class="table-title-4" style="width: 50px;">总分</th>
        </tr>
        <tr>
          <th>建设必要性</th>
          <th>根据省公司部门文件要求，涉及部门考核指标、涉及业务风险的，提供文件依据</th>
          <th>【0-20】<br>提供文件得满分</th>
          <th><input type="text" placeholder="中国电信XXX" class="borderless-input" v-model="input_1_1"></th>
          <th>文件号</th>
          <th>{{ output_1 }}</th>
          <th rowspan="18">{{ output }}</th>
        </tr>
        <tr>
          <th rowspan="3">建设合理性</th>
          <th>需求生命周期</th>
          <th>【0-5】<br>6个月以下，0<br>6个月-1年，3<br>一年以上，5</th>
          <th><input type="text" placeholder="15" class="borderless-input" v-model="input_2_1"></th>
          <th>请填写具体时间<br><input type="text" placeholder="（单位：月）" class="borderless-input" v-model="input_2_2"></th>
          <th>{{ output_2 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>投资估算<br>（横向对比情况）</th>
          <th>【0-5】<br>高于兄弟省份20%以上，0<br>高于兄弟省份5%以上，3<br>低于5%以及小于其他省份投资，5</th>
          <th><input type="text" placeholder="0%" class="borderless-input" v-model="input_3_1"></th>
          <th>填写0%~50%<br><input type="text" placeholder="（省份:河北)" class="borderless-input" v-model="input_3_2"></th>
          <th>{{ output_3 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>使用部门评价意见</th>
          <th>【0-5】<br>一般，0;良好，5;优秀，10</th>
          <th><input type="text" placeholder="优秀" class="borderless-input" v-model="input_4_1"></th>
          <th>评价部门意见与打分部门<br><input type="text" placeholder="（XX部门）" class="borderless-input" v-model="input_4_1"></th>
          <th>{{ output_4 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th rowspan="2">效率</th>
          <th>（前期项目）当前进度</th>
          <th>【0-10】<br>项目未完工，2<br>项目已完工，5<br>项目已验收，9<br>项目已关闭，10<br>新立项项目，10</th>
          <th><input type="text" placeholder="项目已关闭" class="borderless-input" v-model="input_5_1"></th>
          <th>填写前期项目当前进度</th>
          <th>{{output_5}}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>（前期项目）后评价结果</th>
          <th>【0-10】<br>后评价得分(0-60)，5<br>后评价得分(61-80)，8<br>后评价得分(81-100),10<br>新立项项目，10</th>
          <th><input type="text" placeholder="85" class="borderless-input" v-model="input_6_1"></th>
          <th>填写上一期项目后评价得分</th>
          <th>{{ output_6 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th rowspan="5">效果</th>
          <th>增收（含收入增加、挽回收入损失）OR降本（含人工成本）/每年</th>
          <th>【0-5】<br>5万以下，0<br>5万-20万，2<br>20万-50万，3<br>50万以上，5</th>
          <th><input type="text" placeholder="50" class="borderless-input" v-model="input_7_1"></th>
          <th>填写具体指标与金额，单位：万元<br><input type="text" placeholder="（收入增加/挽回收入损失/降本）" class="borderless-input" v-model="input_7_2"></th>
          <th>{{ output_7 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>使用效率提升（加载速度提升、压降人工占比、扩大支撑场景、人工环节减少）</th>
          <th>【0-5】<br>小于1%，1<br>1%-5%，3<br>5%-10%，4<br>大于10%，5</th>
          <th><input type="text" placeholder="15%" class="borderless-input" v-model="input_8_1"></th>
          <th>填写具体指标与类型<br><input type="text" placeholder="（XXXXXX）" class="borderless-input" v-model="input_8_1"></th>
          <th>{{ output_8 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>客户服务指标影响（如满意度增加比例/客户保有量提升/减少客户流失率等任选其一）</th>
          <th>【0-5】<br>小于1%，1<br>1%-5%，3<br>5%-10%，4<br>大于10%，5</th>
          <th><input type="text" placeholder="15%" class="borderless-input" v-model="input_9_1"></th>
          <th>填写具体指标与类型<br><input type="text" placeholder="（XXXXXX）" class="borderless-input" v-model="input_9_2"></th>
          <th>{{ output_9 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>其他指标影响/能力提升-1</th>
          <th>【0-5】<br>小于1%，1<br>1%-5%，3<br>5%-10%，4<br>大于10%，5</th>
          <th><input type="text" placeholder="15%" class="borderless-input" v-model="input_10_1"></th>
          <th>填写具体指标与类型<br><input type="text" placeholder="（XXXXXX）" class="borderless-input" v-model="input_10_2"></th>
          <th>{{ output_10 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>其他指标影响/能力提升-2</th>
          <th>【0-5】<br>小于1%，1<br>1%-5%，3<br>5%-10%，4<br>大于10%，5</th>
          <th><input type="text" placeholder="15%" class="borderless-input" v-model="input_11_1"></th>
          <th>填写具体指标与类型<br><input type="text" placeholder="（XXXXXX）" class="borderless-input" v-model="input_11_2"></th>
          <th>{{ output_11 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th rowspan="3">规划衔接</th>
          <th>是否通过云网发展规划上报集团</th>
          <th>【0-5】<br>否，0;是，5</th>
          <th><input type="text" placeholder="是" class="borderless-input" v-model="input_12_1"></th>
          <th>选择是否</th>
          <th>{{ output_12 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>三滚规划、年度计划与实际立项需求是否一致</th>
          <th>【0-5】<br>完全不一致，0<br>基本一致，80<br>完全一致，100</th>
          <th><input type="text" placeholder="完全一致" class="borderless-input" v-model="input_13_1"></th>
          <th>选择完全一致、基本一致、完全一致</th>
          <th>{{ output_13 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th>三滚规划、年度计划与实际立项金额偏离</th>
          <th>【0-5】<br>±80%，20<br>±50%，50<br>±30%，80<br>±10%，100</th>
          <th><input type="text" placeholder="10%" class="borderless-input" v-model="input_14_1"></th>
          <th>填写偏离度</th>
          <th>{{ output_14 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th rowspan="4">后评价闭环</th>
          <th rowspan="4">基本信息是否完善</th>
          <th rowspan="4">【0-10】<br>内容缺失，0<br>填写完毕无缺项，10</th>
          <th><input type="text" placeholder="填写内容完毕无缺项" class="borderless-input" v-model="input_15_1"></th>
          <th>项目三级功能点数<br><input type="text" placeholder="（XX个）" class="borderless-input" v-model="input_15_2"></th>
          <th>{{ output_15 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th style="display: none;">2</th>
          <th style="display: none;">3</th>
          <th><input type="text" placeholder="中国电信XXX" class="borderless-input" v-model="input_16_1"></th>
          <th>接口建设/改造数<br><input type="text" placeholder="（XX个）" class="borderless-input" v-model="input_16_1"></th>
          <th>{{ output_16 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th style="display: none;">2</th>
          <th style="display: none;">3</th>
          <th><input type="text" placeholder="中国电信XXX" class="borderless-input" v-model="input_17_1"></th>
          <th>预计工作日平均登录次数<br><input type="text" placeholder="（XX次）" class="borderless-input" v-model="input_17_2"></th>
          <th>{{ output_17 }}</th>
          <th style="display: none;">7</th>
        </tr>
        <tr>
          <th style="display: none;">1</th>
          <th style="display: none;">2</th>
          <th style="display: none;">3</th>
          <th><input type="text" placeholder="中国电信XXX" class="borderless-input" v-model="input_18_1"></th>
          <th>建设目标<br><input type="text" placeholder="（通过本期工程的建设，能够达到XXXXXX）" class="borderless-input" v-model="input_18_1"></th>
          <th>{{ output_18 }}</th>
          <th style="display: none;">7</th>
        </tr>
      </table>
    <!-- </div> -->
    </div>
  </div>
</template>

<script>

  import { ref } from 'vue';
  import jsPDF from 'jspdf';
  import html2canvas from 'html2canvas';
  import VueHtmlToPaper from 'vue-html-to-paper';


  export default {
  methods: {
    mycompu(){
      if(this.output_1 != null){
        this.output_1 = this.input_1_1
      }else{
        this.output_1 = '0'
      }

      

      setTimeout(() => {
        this.exportPDF()
      }, 1000)

    },
    async exportPDF() {     
      const content = this.$refs.pdfContent;
      const canvas = await html2canvas(content);
      const imgData = canvas.toDataURL('image/png');
      const doc = new jsPDF({
        orientation: 'portrait',
        unit: 'px',
        format: 'a4',
      });
      const imgProps= doc.getImageProperties(imgData);
      const pdfWidth = doc.internal.pageSize.getWidth();
      const pdfHeight = (imgProps.height * pdfWidth) / imgProps.width;
      doc.addImage(imgData, 'PNG', 0, 0, pdfWidth, pdfHeight);
      doc.save('download.pdf');
    },
   
  },
  data(){
    return{
      input_1_1 : '',
      output_1 : '0',
      input_2_1 : '',
      input_2_2 : '',
      output_2 : '0',
      input_3_1 : '',
      input_3_2 : '',
      output_3 : '0',
      input_4_1 : '',
      input_4_2 : '',
      output_4 : '0',
      input_5_1 : '',
      output_5 : '0',
      input_6_1 : '',
      output_6 : '0',
      input_7_1 : '',
      input_7_2 : '',
      output_7 : '0',
      input_8_1 : '',
      input_8_2 : '',
      output_8 : '0',
      input_9_1 : '',
      input_9_2 : '',
      output_9 : '0',
      input_10_1 : '',
      input_10_2 : '',
      output_10 : '0',
      input_11_1 : '',
      input_11_2 : '',
      output_11 : '0',
      input_12_1 : '',
      output_12 : '0',
      input_13_1 : '',
      output_13 : '0',
      input_14_1 : '',
      output_14 : '0',
      input_15_1 : '',
      input_15_2 : '',
      output_15 : '0',
      input_16_1 : '',
      input_16_2 : '',
      output_16 : '0',
      input_17_1 : '',
      input_17_2 : '',
      output_17 : '0',
      input_18_1 : '',
      input_18_2 : '',
      output_18 : '0',
      output : '0'
    }
  }
};


</script>


<style scoped>

/* 全局表样式 */
.table {
  border-collapse: collapse;
  width: 100%;
  padding: 8px;
}

/* 第一行样式 */
.table-title-1{
  background-color: rgb(185, 255, 207);
  font-weight: bold;
}

/* 第二行前半段样式 */
.table-title-2{
  background-color: rgb(252, 255, 208);
}

/* 第二行后半段样式 */
.table-title-3{
  background-color: rgb(188, 215, 255);
}

/* 评分样式 */
.table-title-4{
  background-color: rgb(255, 194, 194);
}

/* 输入框两行显示 */
input[type="text"]::placeholder {
  white-space: pre-wrap; 
  word-wrap: break-word;
}

input[type="text"] {
  height: 30px;
  line-height: 15px;
  padding: 0;
}

/* 输入框无边框样式 */
.borderless-input {
  border: none;
  text-align: center;
  white-space: pre-wrap;
  outline: none; 
  color:cornflowerblue;
  font-weight: bold;
  width: 300px;
}

th {
  font-size: 15px; /* 默认字体大小 */
}

button{
  background-color: rgb(0, 0, 0);
  border-color: black;
  color: aliceblue;
}

</style>


