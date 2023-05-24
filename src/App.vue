<template>
  <header class="logoBar"></header>
  <section class="content">
    <router-view />
  </section>
</template>

<script>
import { defineComponent, provide, reactive, toRefs, watch } from 'vue';
export default defineComponent({
  setup() {
    const pageConfig = reactive({
      formData: {
        projectProvince: '',
        projectCity: '',
        projectArea: '',
        goodsType: '微模块数据中心',
      },
      list: [
        {
          label: '微模块数据中心',
          imgUrl: require('./img/u665.jpg').default,
          menuList: [
            {
              label: '机柜通道系统',
              widgetList: [
                {
                  type: 'CustomSlider',
                  id: '123216541121231',
                  config: {
                    formMap: {
                      name: 'itgsl',
                      value: 5,
                      type: 'number',
                    },
                    customValida: {
                      codeString: `
                        if({{itgsl}} * {{itgdgfz}} >= 250){
                          ElMessage.warning('IT柜数量 * IT单柜功率 要小于 250，请重新选择');
                          setTimeout(()=>{
                            ##itgsl##.config.formMap.value = ##itgsl##.config.min;
                          },300);
                          return;
                        }
                      `,
                    },
                    min: 5,
                    max: 36,
                    step: 1,
                    tips: '用户根据需求确定需要配置的IT机柜数量用来放置服务器；若微模块中所有柜位数量为奇数两边不对称时系统会在额外多配置一台IT机柜',
                    label: '所需IT柜数量',
                    defaultVal: 20,
                  },
                },
                {
                  type: 'CustomSlider',
                  id: '1232165322321121231',
                  config: {
                    formMap: {
                      name: 'itgdgfz',
                      value: 3,
                      type: 'number',
                    },
                    customValida: {
                      codeString: `if({{itgsl}} * {{itgdgfz}} >= 250){
                        ElMessage.warning('IT柜数量 * IT单柜功率 要小于 250，请重新选择');
                        setTimeout(()=>{
                          ##itgdgfz##.config.formMap.value = ##itgdgfz##.config.min;
                        },300);
                        return;
                      }`,
                    },
                    min: 3,
                    max: 10,
                    step: 1,
                    tips: '用户根据需求确定微模块中IT机柜的平均功率，IT单柜负载在3-10整数范围内可选，IT单柜负载与所需IT机柜数量的乘积不高于250kva',
                    label: 'IT柜单柜负载（kva）',
                    defaultVal: 20,
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '2243443434321',
                  config: {
                    formMap: {
                      name: 'jgsd',
                      value: '1200',
                    },
                    tips: 'IT机柜深度决定各类机柜深度，空调深度，机柜配件深度',
                    label: 'IT机柜深度(mm)',
                    options: [
                      { label: '1100', value: '1100' },
                      { label: '1200', value: '1200' },
                    ],
                  },
                },
                {
                  type: 'CustomInputCheck',
                  id: '3323241',
                  config: {
                    formMap: {
                      name: 'qzcbsl',
                      value: '',
                      type: 'number',
                    },
                    tips: '需要用户根据实际需求选择是否配置和配置数量',
                    label: '是否配置轻载层板',
                    placeholder: '配置数量',
                  },
                },
                {
                  type: 'CustomInputCheck',
                  id: '5623423423',
                  config: {
                    formMap: {
                      name: 'zzcbsl',
                      value: '',
                      type: 'number',
                    },
                    tips: '需要用户根据实际需求选择是否配置和配置数量',
                    label: '是否配置重载层板',
                    placeholder: '配置数量',
                  },
                },
                {
                  type: 'CustomInputCheck',
                  id: '65422342',
                  config: {
                    formMap: {
                      name: 'lxdgsl',
                      value: '',
                      type: 'number',
                    },
                    tips: '需要用户根据实际需求选择是否配置和配置数量',
                    label: 'L型导轨配置数量',
                    placeholder: '配置数量',
                  },
                },
                {
                  type: 'CustomInputCheck',
                  id: '8765423',
                  config: {
                    formMap: {
                      name: 'oneulxjsl',
                      value: '',
                      type: 'number',
                    },
                    tips: '需要用户根据实际需求选择是否配置和配置数量',
                    label: '1U理线架配置数量',
                    placeholder: '配置数量',
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '111245312132',
                  config: {
                    formMap: {
                      name: 'tdpymlx',
                      value: '',
                    },
                    tips: '手动推拉门为经济性价比方案，自动平移门为高端方案，附带75寸平移门触摸屏',
                    label: '通道门类型',
                    options: [
                      { label: '手动推拉门', value: '手动推拉门' },
                      { label: '自动平移门', value: '自动平移门' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '2443321121',
                  config: {
                    formMap: {
                      name: 'tdlx',
                      value: '',
                    },
                    tips: '单通道适用于有一侧靠墙的组合；双通道适用于两侧都有机柜的通道场合',
                    label: '通道类型',
                    options: [
                      { label: '单通道', value: '单通道' },
                      { label: '双通道', value: '双通道' },
                    ],
                  },
                },
              ],
            },
            {
              label: '配电系统',
              widgetList: [
                {
                  type: 'CustomRadioGroup',
                  id: '65423422',
                  config: {
                    formMap: {
                      name: 'sfpzups',
                      value: '',
                    },
                    customValida: {
                      codeString: `if({{sfpzups}} === '配置'){
                        setTimeout(()=>{
                          ##upswz##.config.hide = false;
                          ##upsryfs##.config.hide = false;
                        },300);
                      }else{
                        setTimeout(()=>{
                          ##upswz##.config.hide = true;
                          ##upsryfs##.config.hide = true;
                          ##upswz##.config.formMap.value='';
                          ##upsryfs##.config.formMap.value='';
                        },300);
                      }`,
                    },
                    tips: '若用户选择了其他品牌的UPS此处选不配置',
                    label: '是否配置UPS',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '65654232',
                  config: {
                    formMap: {
                      name: 'upswz',
                      value: '',
                    },
                    hide: true,
                    tips: 'UPS选择安装在微模块内部时配置模块化插框式UPS放置在配电一体柜中（当30功率模块不超过四个时）或放置在专门的UPS机柜中。UPS选择安装在微模块外部时配置模块化柜式UPS',
                    label: 'UPS安装位置',
                    options: [
                      { label: '微模块内部', value: '微模块内部' },
                      { label: '微模块外部', value: '微模块外部' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '651234232',
                  config: {
                    formMap: {
                      name: 'upsryfs',
                      value: '',
                    },
                    hide: true,
                    tips: '功率模块冗余为功率模块n+1冗余，整机冗余为2n冗余',
                    label: 'UPS冗余方式',
                    options: [
                      { label: '功率模块冗余', value: '功率模块冗余' },
                      { label: '整机冗余', value: '整机冗余' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '8765654232',
                  config: {
                    formMap: {
                      name: 'sfyxdc',
                      value: '',
                    },
                    customValida: {
                      codeString: `if({{sfyxdc}} === '配置'){
                        if({{itgsl}} * {{itgdgfz}} <= 25){
                          setTimeout(()=>{
                            ##xdcwz##.config.hide = false;
                          },300);
                        }
                        setTimeout(()=>{
                            ##upshbsj##.config.hide = false;
                        },300);
                      }else{
                        setTimeout(()=>{
                          ##upshbsj##.config.hide = true;
                          ##upshbsj##.config.formMap.value='';
                          ##xdcwz##.config.hide = true;
                          ##xdcwz##.config.formMap.value='';
                        },300);
                      }`,
                    },
                    tips: '单微模块最多可配置四组40节250AH蓄电池',
                    label: '是否配置蓄电池',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '876565765444232',
                  config: {
                    formMap: {
                      name: 'upshbsj',
                      value: '',
                      type: 'number',
                    },
                    customValida: {
                      codeString: `
                        if(
                          ({{itgsl}} * {{itgdgfz}} <= 25) ||
                          ({{itgsl}} * {{itgdgfz}} > 25 && {{itgsl}} * {{itgdgfz}} <= 30 && ['30','60'].includes({{upshbsj}})) ||
                          ({{itgsl}} * {{itgdgfz}} > 30 && {{itgsl}} * {{itgdgfz}} <= 60 && ['30'].includes({{upshbsj}}))
                        ){
                          ##xdcwz##.config.hide = false;
                        }else{
                          ##xdcwz##.config.hide = true;
                          ##xdcwz##.config.formMap.value='';
                        }

                        let condition = [];
                        if({{itgsl}} * {{itgdgfz}} >= 240){
                          condition = [
                            { label: '30', value: '30' },
                            { label: '60', value: '60' },
                          ];
                        }else if({{itgsl}} * {{itgdgfz}} >= 145){
                          condition = [
                            { label: '30', value: '30' },
                          ];
                        }else{
                          condition = [
                            { label: '30', value: '30' },
                            { label: '60', value: '60' },
                            { label: '120', value: '120' },
                          ];
                        }
                        ##upshbsj##.config.options = condition;
                        ##upshbsj##.config.formMap.value='';
                      `,
                    },
                    hide: true,
                    tips: '此项决定了蓄电池的规格和配置数量，后备时间可选范围随着机房总负载的大小进行改变，若没有所需的UPS后备时间选项可联系共济售前进行非标设计',
                    label: 'UPS后备时间(分钟)',
                    options: [
                      { label: '30', value: '30' },
                      { label: '60', value: '60' },
                      { label: '120', value: '120' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '876999565765444232',
                  config: {
                    formMap: {
                      name: 'xdcwz',
                      value: '',
                    },
                    hide: true,
                    tips: '微模块内最多可放置2个电池柜用于蓄电池的放置，若机房总负载超过60kva则蓄电池安装位置默认放置在微模块外部',
                    label: '蓄电池安装位置',
                    options: [
                      { label: '微模块内部', value: '微模块内部' },
                      { label: '微模块外部', value: '微模块外部' },
                    ],
                  },
                },
              ],
            },
            {
              label: '空调系统',
              widgetList: [
                {
                  type: 'CustomRadioGroup',
                  id: '8765657654232',
                  config: {
                    formMap: {
                      name: 'sfpzktcp',
                      value: '',
                    },
                    customValida: {
                      codeString: `if({{sfpzktcp}} === '配置'){
                        setTimeout(()=>{
                          ##ktlx##.config.hide = false;
                          ##ktnwjczjj##.config.hide = false;
                          ##ktnwjspjj##.config.hide = false;
                        },300);
                      }else{
                        setTimeout(()=>{
                          ##ktlx##.config.hide = true;
                          ##ktnwjczjj##.config.hide = true;
                          ##ktnwjspjj##.config.hide = true;
                          ##ktlx##.config.formMap.value='';
                          ##ktnwjczjj##.config.formMap.value='';
                          ##ktnwjspjj##.config.formMap.value='';
                        },300);
                      }`,
                    },
                    tips: '用户若已选择其他品牌的空调此处可选择不配置',
                    label: '是否配置空调产品',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomBtnGroup',
                  id: '54238765256',
                  config: {
                    formMap: {
                      name: 'ktlx',
                      value: '',
                    },
                    customValida: {
                      codeString: `if(['恒温恒湿底座空调','单冷底座空调'].includes({{ktlx}})){
                        setTimeout(()=>{
                          ##sfpzwmkdz##.config.disable = true;
                          ##sfpzwmkdz##.config.formMap.value='配置';
                        },300);
                      }else if(['恒温恒湿列间空调','单冷列间空调'].includes({{ktlx}})){
                        setTimeout(()=>{
                          ##sfpzwmkdz##.config.disable = false;
                          ##sfpzwmkdz##.config.formMap.value='';
                        },300);
                      }`,
                    },
                    hide: true,
                    tips: '有加湿需求的选择恒温恒湿型空调，无额外加湿需求的选择单冷型空调。底座空调不占用柜位空间，制冷更均衡，当IT单柜负载高于6kva时底座空调默认不可选',
                    label: '空调产品选型',
                    options: [
                      { label: '恒温恒湿列间空调', value: '恒温恒湿列间空调' },
                      { label: '单冷列间空调', value: '单冷列间空调' },
                      { label: '恒温恒湿底座空调', value: '恒温恒湿底座空调' },
                      { label: '单冷底座空调', value: '单冷底座空调' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '876565765654232',
                  config: {
                    formMap: {
                      name: 'sfpzwmkdz',
                      value: '',
                    },
                    tips: '选配底座空调时默认配置底座，选择列间空调时根据用户需求选择是否需要配置底座',
                    label: '是否配置微模块底座',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '567767622',
                  config: {
                    formMap: {
                      name: 'xdwz',
                      value: '',
                    },
                    customValida: {
                      codeString: `
                        if({{xdwz}} === '正落差'){
                          ##ktnwjczjj##.config.max = 5;
                          ##ktnwjczjj##.config.hide = true;
                          setTimeout(()=>{
                            ##ktnwjczjj##.config.hide = false;
                          },100);
                        }else if({{xdwz}} === '负落差'){
                          ##ktnwjczjj##.config.max = 20;
                          ##ktnwjczjj##.config.hide = true;
                          setTimeout(()=>{
                            ##ktnwjczjj##.config.hide = false;
                          },100);
                        }
                        if({{xdwz}} === '正落差'&&Number({{ktnwjczjj}})>5){
                          ##ktnwjczjj##.config.formMap.value = 5;
                        }else if({{xdwz}} === '负落差'&&Number({{ktnwjczjj}})>20){
                          ##ktnwjczjj##.config.formMap.value = 20;
                        }
                      `,
                    },
                    tips: '正落差指室内机位于室外机上方；负落差指室内机位于室外机下方',
                    label: '相对位置',
                    options: [
                      { label: '正落差', value: '正落差' },
                      { label: '负落差', value: '负落差' },
                    ],
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '87656576543654232',
                  config: {
                    formMap: {
                      name: 'ktnwjczjj',
                      value: 0,
                      type: 'number',
                    },
                    hide: true,
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 20,
                    tips: '指空调内外机之间的垂直距离，用于确定铜管等物料的配置信息',
                    label: '空调内外机垂直距离',
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '8765432165654232',
                  config: {
                    formMap: {
                      name: 'ktnwjspjj',
                      value: 0,
                      type: 'number',
                    },
                    hide: true,
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 60,
                    tips: '指空调内外机之间的水平距离，用于确定铜管等物料的配置信息',
                    label: '空调内外机水平距离',
                  },
                },
              ],
            },
            {
              label: '监控系统',
              widgetList: [
                {
                  type: 'CustomRadioGroup',
                  id: '76523422',
                  config: {
                    formMap: {
                      name: 'sfpzzcjc',
                      value: '',
                    },
                    tips: '资产检测：U位级资产定位，实时盘点，自动检测',
                    label: '是否配置资产检测',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '0987622',
                  config: {
                    formMap: {
                      name: 'isSetBatteryMonitor',
                      value: '',
                    },
                    customValida: {
                      codeString: `if({{sfyxdc}} === '不配置' && {{isSetBatteryMonitor}} == 'true'){
                        console.log({{sfyxdc}},{{isSetBatteryMonitor}})
                        ##xdczzs##.config.hide = false;
                        ##xdczjs##.config.hide = false;
                      }else{
                        console.log({{sfyxdc}},{{isSetBatteryMonitor}})
                        setTimeout(()=>{
                          ##xdczzs##.config.hide = true;
                          ##xdczjs##.config.hide = true;
                          ##xdczzs##.config.formMap.value='';
                          ##xdczjs##.config.formMap.value='';
                        },100);
                      }`,
                    },
                    tips: '蓄电池BMS，实时监测电池温度、内阻，电压、电流等参数，基于大数据分析智能判断电池运行健康状况，确保供电系统的整体安全',
                    label: '是否配置蓄电池检测',
                    options: [
                      { label: '配置', value: true },
                      { label: '不配置', value: false },
                    ],
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '872222656576543654232',
                  config: {
                    formMap: {
                      name: 'xdczzs',
                      value: 0,
                      type: 'number',
                    },
                    hide: true,
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 100,
                    tips: '请输入需要检测的蓄电池的总组数',
                    label: '蓄电池总组数',
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '8765657444446543654232',
                  config: {
                    formMap: {
                      name: 'xdczjs',
                      value: 0,
                      type: 'number',
                    },
                    hide: true,
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 100,
                    tips: '请输入需要检测的蓄电池的总节数',
                    label: '蓄电池总节数',
                  },
                },
                {
                  type: 'CustomSlider',
                  id: '12321112129992331',
                  config: {
                    formMap: {
                      name: 'sxtgs',
                      value: 2,
                      type: 'number',
                    },
                    customValida: {
                      // ##name## => 获取这个组件的配置
                      codeString: `
                        let condition = [];
                        if({{sxtgs}}<=10){
                          condition = [
                            { label: '15', value: '15' },
                            { label: '30', value: '30' },
                            { label: '60', value: '60' },
                            { label: '90', value: '90' },
                            { label: '120', value: '120' },
                            { label: '180', value: '180' },
                          ];
                        }else if({{sxtgs}}>=11&&{{sxtgs}}<=16){
                          condition = [
                            { label: '15', value: '15' },
                            { label: '30', value: '30' },
                            { label: '60', value: '60' },
                            { label: '90', value: '90' },
                            { label: '120', value: '120' },
                          ];
                        }else if({{sxtgs}}>=17&&{{sxtgs}}<=21){
                          condition = [
                            { label: '15', value: '15' },
                            { label: '30', value: '30' },
                            { label: '60', value: '60' },
                            { label: '90', value: '90' },
                          ];
                        }else if({{sxtgs}}>=22&&{{sxtgs}}<=32){
                          condition = [
                            { label: '15', value: '15' },
                            { label: '30', value: '30' },
                            { label: '60', value: '60' },
                          ];
                        }
                        ##ccts##.config.options = condition;
                        ##ccts##.config.formMap.value='';
                      `,
                    },
                    min: 1,
                    max: 32,
                    step: 1,
                    tips: '摄像头配置个数1——32个可选，视频格式1080p',
                    label: '摄像头配置个数',
                    defaultVal: 20,
                  },
                },
                {
                  type: 'CustomBtnGroup',
                  id: '5423256',
                  config: {
                    formMap: {
                      name: 'ccts',
                      value: '',
                      type: 'number',
                    },
                    tips: '用户根据自身存储需求选择摄像头录像视频需要存储的时间',
                    label: '视频存储时间(天)',
                    options: [
                      { label: '15', value: '15' },
                      { label: '30', value: '30' },
                      { label: '60', value: '60' },
                      { label: '90', value: '90' },
                      { label: '120', value: '120' },
                      { label: '180', value: '180' },
                    ],
                  },
                },
              ],
            },
          ],
        },
        {
          label: '一体化柜数据中心',
          imgUrl: require('./img/u666.png').default,
          menuList: [
            {
              label: '机柜系统',
              widgetList: [
                {
                  type: 'CustomSlider',
                  id: '123211122455551231',
                  config: {
                    formMap: {
                      name: 'itgsl',
                      value: 0,
                      type: 'number',
                    },
                    customValida: {
                      codeString: `
                        if({{itgsl}}>=0 && {{itgsl}}<=5){
                          ##itgdgfz##.config.min = 2;
                          ##itgdgfz##.config.max = 5;
                          ##itgdgfz##.config.formMap.value = 2;
                        }else if({{itgsl}}>=6 && {{itgsl}} <=7){
                          ##itgdgfz##.config.min = 2;
                          ##itgdgfz##.config.max = 4;
                          ##itgdgfz##.config.formMap.value = 4;
                        }else{
                          ##itgdgfz##.config.min = 2;
                          ##itgdgfz##.config.max = 3;
                          ##itgdgfz##.config.formMap.value = 3;
                        }
                      `,
                    },
                    min: 0,
                    max: 9,
                    step: 1,
                    tips: 'IT机柜数量可选范围0—9，当IT机柜数量选择为0时，只配置一台综合机柜',
                    label: '所需IT柜数量',
                    defaultVal: 20,
                  },
                },
                {
                  type: 'CustomSlider',
                  id: '123211121231',
                  config: {
                    formMap: {
                      name: 'itgdgfz',
                      value: '2',
                    },
                    min: 2,
                    max: 5,
                    step: 1,
                    tips: 'IT单柜负载范围在2—5范围可选，且IT单柜负载*所需IT机柜数量<=28',
                    label: 'IT柜单柜负载（kva）',
                    defaultVal: 2,
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '0988767622',
                  config: {
                    formMap: {
                      name: 'itglx',
                      value: '',
                    },
                    tips: '标准机柜：综合机柜配置10.1英寸屏开孔，IT机柜为标准玻璃门；智慧机柜：综合机柜配置15.6寸屏开孔，IT机柜为铝合金外框的玻璃门',
                    label: '机柜类型',
                    options: [
                      { label: '标准机柜', value: '标准机柜' },
                      { label: '智慧机柜', value: '智慧机柜' },
                    ],
                  },
                },
              ],
            },
            {
              label: '配电系统',
              widgetList: [
                {
                  type: 'CustomRadioGroup',
                  id: '9887676547622',
                  config: {
                    formMap: {
                      name: 'sfpzups',
                      value: '',
                    },
                    tips: '若用户选择了其他品牌的UPS此处选不配置。UPS功率3～30KVA可选',
                    label: '是否配置UPS',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '76543465432',
                  config: {
                    formMap: {
                      name: 'sfyxdc',
                      value: '',
                    },
                    customValida: {
                      codeString: `
                        if({{sfyxdc}} === '配置'){
                          ##upshbsj##.config.hide = false;
                        }else if({{sfyxdc}} === '不配置'){
                          ##upshbsj##.config.formMap.value = '';
                          ##upshbsj##.config.hide = true;
                        }
                      `,
                    },
                    tips: '用户根据实际需求选择是否需要配置蓄电池，蓄电池默认使用电池柜放置，且联柜中的电池柜数量最多配置2个',
                    label: '是否配置蓄电池',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '876565765753444232',
                  config: {
                    formMap: {
                      name: 'upshbsj',
                      value: '',
                    },
                    hide: true,
                    tips: '此项决定了蓄电池的规格和配置数量，以及确定电池柜配置数量',
                    label: 'UPS后备时间(分钟)',
                    options: [
                      { label: '15', value: '15' },
                      { label: '30', value: '30' },
                      { label: '60', value: '60' },
                      { label: '120', value: '120' },
                    ],
                  },
                },
              ],
            },
            {
              label: '空调系统',
              widgetList: [
                {
                  type: 'CustomBtnGroup',
                  id: '5423256',
                  config: {
                    formMap: {
                      name: 'ktlx',
                      value: '',
                    },
                    tips: '有加湿需求的选择恒温恒湿型机架式空调，无额外加湿需求的选择恒温型机架式空调，机架式空调规格3.5/6.5/12.5kw，根据IT机柜数量，IT单柜负载系统自动选配合适的型号和数量',
                    label: '空调产品选型',
                    options: [
                      { label: '恒温恒湿型', value: '恒温恒湿型' },
                      { label: '恒温型', value: '恒温型' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '567767622',
                  config: {
                    formMap: {
                      name: 'xdwz',
                      value: '',
                    },
                    customValida: {
                      codeString: `
                        if({{xdwz}} === '正落差'){
                          ##ktnwjczjj##.config.max = 15;
                          ##ktnwjczjj##.config.hide = true;
                          setTimeout(()=>{
                            ##ktnwjczjj##.config.hide = false;
                          },100);
                        }else if({{xdwz}} === '负落差'){
                          ##ktnwjczjj##.config.max = 20;
                          ##ktnwjczjj##.config.hide = true;
                          setTimeout(()=>{
                            ##ktnwjczjj##.config.hide = false;
                          },100);
                        }
                        if({{xdwz}} === '正落差'&&Number({{ktnwjczjj}})>15){
                          ##ktnwjczjj##.config.formMap.value = 15;
                        }else if({{xdwz}} === '负落差'&&Number({{ktnwjczjj}})>20){
                          ##ktnwjczjj##.config.formMap.value = 20;
                        }
                      `,
                    },
                    tips: '正落差指室内机位于室外机上方；负落差指室内机位于室外机下方',
                    label: '相对位置',
                    options: [
                      { label: '正落差', value: '正落差' },
                      { label: '负落差', value: '负落差' },
                    ],
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '879876565654232',
                  config: {
                    formMap: {
                      name: 'ktnwjczjj',
                      value: '',
                    },
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 20,
                    tips: '选正落差时空调内外机垂直距离最大值为15m，选负落差时空调内外机垂直距离最大值为20m',
                    label: '空调内外机垂直距离',
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '4565654232',
                  config: {
                    formMap: {
                      name: 'ktnwjspjj',
                      value: '',
                    },
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 50,
                    tips: '空调内外机水平距离最大为50m',
                    label: '空调内外机水平距离',
                  },
                },
              ],
            },
            {
              label: '监控系统',
              widgetList: [
                {
                  type: 'CustomRadioGroup',
                  id: '111113232121',
                  config: {
                    formMap: {
                      name: 'sfpzzcjc',
                      value: '',
                    },
                    tips: '资产检测物料包含FAU-A现场采集单元，资产检测终端，EIC电子标签',
                    label: '是否配置资产检测',
                    options: [
                      { label: '配置', value: '配置' },
                      { label: '不配置', value: '不配置' },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '45452312123131231',
                  config: {
                    formMap: {
                      name: 'isSetLeakMonitor',
                      value: '',
                    },
                    tips: '漏水检测物料包含水浸传感器，漏水绳',
                    label: '是否配置漏水检测',
                    options: [
                      { label: '配置', value: true },
                      { label: '不配置', value: false },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '22238888523232',
                  config: {
                    formMap: {
                      name: 'isSetBatteryMonitor',
                      value: '',
                    },
                    customValida: {
                      codeString: `if({{sfyxdc}} === '不配置' && {{isSetBatteryMonitor}} == 'true'){
                        console.log({{sfyxdc}},{{isSetBatteryMonitor}})
                        ##xdczzs##.config.hide = false;
                        ##xdczjs##.config.hide = false;
                      }else{
                        console.log({{sfyxdc}},{{isSetBatteryMonitor}})
                        setTimeout(()=>{
                          ##xdczzs##.config.hide = true;
                          ##xdczjs##.config.hide = true;
                          ##xdczzs##.config.formMap.value='';
                          ##xdczjs##.config.formMap.value='';
                        },100);
                      }`,
                    },
                    tips: '蓄电池检测物料包含智能网关，蓄电池内阻采集模块，电池组电流采集模块',
                    label: '是否配置蓄电池检测',
                    options: [
                      { label: '配置', value: true },
                      { label: '不配置', value: false },
                    ],
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '872222656576543654232',
                  config: {
                    formMap: {
                      name: 'xdczzs',
                      value: 0,
                      type: 'number',
                    },
                    hide: true,
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 100,
                    tips: '请输入需要检测的蓄电池的总组数',
                    label: '蓄电池总组数',
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '8765657444446543654232',
                  config: {
                    formMap: {
                      name: 'xdczjs',
                      value: 0,
                      type: 'number',
                    },
                    hide: true,
                    precision: 0,
                    step: 1,
                    min: 0,
                    max: 100,
                    tips: '请输入需要检测的蓄电池的总节数',
                    label: '蓄电池总节数',
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '2611126853',
                  config: {
                    formMap: {
                      name: 'isSetFireMonitor',
                      value: '',
                    },
                    tips: '消防感温灭火一体机1.8/3.6/5.4L可选，内置七氟丙烷',
                    label: '是否配置消防检测',
                    options: [
                      { label: '配置', value: true },
                      { label: '不配置', value: false },
                    ],
                  },
                },
                {
                  type: 'CustomRadioGroup',
                  id: '012435988767622',
                  config: {
                    formMap: {
                      name: 'isSetVideoMonitor',
                      value: '',
                    },
                    customValida: {
                      codeString: `
                        if({{isSetVideoMonitor}} == true){
                            ##sxtgs##.config.hide = false;
                        }else if({{isSetVideoMonitor}} == false){
                          ##sxtgs##.config.hide = true;
                        }
                      `,
                    },
                    tips: '视频检测物料包含摄像头，摄像头安装机架，交换机，网络硬盘录像机，硬盘录像机安装支架，专用硬盘等',
                    label: '是否配置视频检测',
                    options: [
                      { label: '配置', value: true },
                      { label: '不配置', value: false },
                    ],
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '4565654232',
                  config: {
                    formMap: {
                      name: 'sxtgs',
                      value: '',
                    },
                    tips: '摄像头配置个数1——32个可选，视频格式1080p',
                    label: '摄像头配置个数',
                  },
                },
                {
                  type: 'CustomNumberInput',
                  id: '8886544677',
                  config: {
                    formMap: {
                      name: 'ythgpzts',
                      value: '',
                      type: 'number',
                    },
                    step: 1,
                    min: 1,
                    tips: '若用户同种配置需要多套时可在此输入需要配置的套数',
                    label: '一体化柜配置套数',
                  },
                },
              ],
            },
          ],
        },
      ],
    });

    provide('pageConfig', pageConfig);
  },
});
</script>

<style lang="less">
html,
body,
#app {
  height: 100%;
  margin: 0;
  overflow: hidden;
}
.logoBar {
  height: 40px;
  text-align: center;
  background: dimgray;
  background-image: url("./img/logo.png");
  background-repeat: no-repeat;
  background-size: 150px;
  background-position-x: 50%;
  background-position-y: 6px;
}
.content {
  height: calc(100% - 40px);
}
</style>
