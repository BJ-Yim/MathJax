<template>
  <div id="app">
    <div v-html="tex"></div>
    <div>$\alpha+\beta=\gamma$</div>
    <router-view/>
    <div class="volume" v-for="(volume, vix) in volumes" :key="vix">
        <div v-if="partsList.indexOf('volumes')>=0 && volume.blocks.length>0">
            <h1 class="volume-title" style="margin: 10px auto 1px">
                <span class="volume-title">{{volume.title}}</span>
            </h1>
            <h3 class="volume-note">
                <span style="padding-left: 2px">{{volume.note}}</span>
            </h3>
        </div>
        <div v-for="(block, bix) in volume.blocks" :key="bix">
            <div v-if="partsList.indexOf('blocks')>=0 && block.questions.length>0" class="paper-block _edit" @click="settingList.subHead=true">（共 小题
                <span>，每小题
                  <span style="display: inline-block">  分</span>
                </span>
                ，共  分
                <span v-if="block.note!=''">，</span>
                <span v-if="block.note!=''"></span>
                ）
            </div>
            <div v-for="(question, index) in block.questions" class="all" :key="index">
                <tiku-question v-bind:class="{linkChecked:$route.fullPath.indexOf(question.type+index)>=0}" :anchor="question.type+index" :showScore="true" :hideRefer="true" :question="question"></tiku-question>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import TikuQuestion from './components/TikuQuestion.vue';

export default {
  name: 'App',
  data () {
    return {
      tex: '<img src="http://yx-kbs-ks3.haofenshu.com/images/ed642e2c6ce01b770f0aa688d76330cf.png@w=196&h=169" alt="go题库" style="vertical-align:middle;FLOAT:right;"/>某运输装置如图所示，其中钢结构${ABD}$是${AB= BD= l}$，${\angle B= \dfrac{\pi }{3}}$的固定装置，${AB}$上可滑动的点${C}$使${CD}$垂直与底面（${C}$不${A}$，${B}$与重合），且${CD}$可伸缩（当${CD}$伸缩时，装置${ABD}$随之绕${D}$在同一平面内旋转），利用该运输装置可以将货物从地面${D}$处沿${D\rightarrow C\rightarrow A}$运送至${A}$处，货物从${D}$处至${C}$处运行速度为${v}$，从${C}$处至${A}$处运行速度为${3v}$．为了使运送货物的时间${t}$最短，需在运送前调整运输装置中${\angle DCB= \theta }$的大小．',
      haha: "",
      volumes: [],
      "partsList":[
            "name",
            "subtitle",
            "paper_info",
            "gutter",
            "attentions",
            "volumes",
            "blocks",
            "secret_tag"
        ]
    }
  },
  components: {
      TikuQuestion,
  },
  created(){
    this.volumes = [
        {
            "title":"卷I（选择题）",
            "note":"",
            "blocks":[
                {
                    "title":"选择题（本大题共计2小题，每题3分，共计6分）",
                    "note":"",
                    "type":"选择题",
                    "default_score":3,
                    "questions":[
                        {
                            "comment":"本题以命题的真假判断为载体，考查了集合的相关性质，难度不大，属于基础题．",
                            "refer_exampapers":[
                                {
                                    "province":"河北",
                                    "city":"邯郸",
                                    "sch_name":"",
                                    "name":"2016-2017学年河北省邯郸市成安一中高一（上）9月月考数学试卷",
                                    "region":"河北",
                                    "year":2017,
                                    "category":"月考试卷",
                                    "id":821230079
                                },
                                {
                                    "province":"宁夏",
                                    "city":"石嘴山",
                                    "sch_name":"",
                                    "name":"2015-2016学年宁夏石嘴山三中高二（下）期中数学试卷（文科）",
                                    "region":"宁夏",
                                    "year":2016,
                                    "category":"期中试卷",
                                    "id":3442933247
                                }
                            ],
                            "blocks":{
                                "types":[
                                    "选择题"
                                ],
                                "explanations":[
                                    "根据集合元素的确定性、特殊数集、集合相等的概念及子集的概念，逐一分析四个命题的正误，可得答案．"
                                ],
                                "solutions":[
                                    "<div style='visibility: hidden; overflow: hidden; position: absolute; top: 0px; height: 1px; width: auto; padding: 0px; border: 0px; margin: 0px; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal;'><br> </div><p>解：很大的实数不具有确定性，故不能构造集合，故A错误；<br> 自然数集${{\rm N}}$中最小的数是${0}$，故B错误；<br> 集合${{\{y\mathrel{|} y= x^{2}-1\}}}$是数集，集合${{\{(x,\, y)\mathrel{|} y= x^{2}-1\}}}$是点集，不是同一个集合，故C错误；<br> 空集是任何集合的子集，故D正确.<br> 故选D．</p><div style='position: absolute; width: 0px; height: 0px; overflow: hidden; padding: 0px; border: 0px; margin: 0px;'></div>"
                                ],
                                "answers":[
                                    "D"
                                ],
                                "stems":[
                                    {
                                        "options":{
                                            "A":"很大的实数可以构成集合",
                                            "B":" 自然数集<span class='preview-latex' ondblclick='render_immediately(this)' onmouseover='show_preview(event, this)' onmouseout='hide_preview()'>${{\rm N}}$</span>中最小的数是${1}$ ",
                                            "C":" 集合${\{y\mathrel{|} y= x^{2}-1\}}$与集合${\{(x,\, y)\mathrel{|} y= x^{2}-1\}}$是同一个集合 ",
                                            "D":"空集是任何集合的子集．"
                                        },
                                        "stem":"下列命题正确的是（　　）"
                                    }
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "score":0.03,
                                            "chance":0.0058
                                        },
                                        {
                                            "id":2125856767,
                                            "name":"命题的真假判断与应用",
                                            "score":1.37,
                                            "chance":0.2544
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ]
                                ]
                            },
                            "description":"",
                            "type":"选择题",
                            "period":"高中",
                            "difficulty":5,
                            "refer_times":2,
                            "knowledges":[
                                {
                                    "id":2125856767,
                                    "name":"命题的真假判断与应用",
                                    "score":1.37,
                                    "chance":0.2544,
                                    "videos":[

                                    ]
                                },
                                {
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "score":0.03,
                                    "chance":0.0058,
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                }
                            ],
                            "subject":"数学",
                            "elite":1,
                            "core_knowledges":[

                            ],
                            "id":3521626367,
                            "score":3
                        },
                        {
                            "comment":"本题主要借助新定义考查了集合之间的关系的判断，属于基础题．",
                            "refer_exampapers":[
                                {
                                    "province":"甘肃",
                                    "city":"天水",
                                    "sch_name":"",
                                    "name":"2015-2016学年甘肃省天水市秦安二中高一（上）期末数学试卷",
                                    "region":"甘肃",
                                    "year":2016,
                                    "category":"期末试卷",
                                    "id":434503167
                                },
                                {
                                    "province":"甘肃",
                                    "city":"定西",
                                    "sch_name":"",
                                    "name":"2015-2016学年甘肃省定西市通渭县榜罗中学高一（上）期末数学试卷",
                                    "region":"甘肃",
                                    "year":2016,
                                    "category":"期末试卷",
                                    "id":133365247
                                },
                                {
                                    "province":"北京",
                                    "city":"",
                                    "sch_name":"清华附中",
                                    "name":"2014年北京市清华附中高考数学二轮专题训练：集合与逻辑（理科）",
                                    "region":"北京",
                                    "year":2014,
                                    "category":"高考复习",
                                    "id":3674668287
                                },
                                {
                                    "province":"浙江",
                                    "city":"杭州",
                                    "sch_name":"",
                                    "name":"2013-2014学年浙江省杭州高中高一（上）期末数学试卷",
                                    "region":"浙江",
                                    "year":2014,
                                    "category":"期末试卷",
                                    "id":613678847
                                },
                                {
                                    "province":"北京",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2014年北京市清大附中高考数学二轮专题训练：集合与逻辑（理科）",
                                    "region":"北京",
                                    "year":2014,
                                    "category":"高考复习",
                                    "id":2945711359
                                },
                                {
                                    "province":"浙江",
                                    "city":"杭州",
                                    "sch_name":"",
                                    "name":"2013-2014学年浙江省杭州市富阳二中高三（下）周练数学试卷（文科）（4）",
                                    "region":"浙江",
                                    "year":2014,
                                    "category":"单元测试",
                                    "id":2573990911
                                },
                                {
                                    "province":"广西",
                                    "city":"南宁",
                                    "sch_name":"南宁二中",
                                    "name":"2011-2012学年广西南宁二中高三（上）10月月考数学试卷（文科）",
                                    "region":"广西",
                                    "year":2012,
                                    "category":"月考试卷",
                                    "id":2138897151
                                },
                                {
                                    "province":"广西",
                                    "city":"南宁",
                                    "sch_name":"南宁二中",
                                    "name":"2011-2012学年广西南宁二中高三（上）10月月考数学试卷（理科）",
                                    "region":"广西",
                                    "year":2012,
                                    "category":"月考试卷",
                                    "id":2580020223
                                },
                                {
                                    "province":"湖北",
                                    "city":"黄石",
                                    "sch_name":"",
                                    "name":"2011-2012学年湖北省黄石市大冶市华中学校高三数学滚动训练（三）",
                                    "region":"湖北",
                                    "year":2012,
                                    "category":"高考复习",
                                    "id":3899063295
                                },
                                {
                                    "province":"广西",
                                    "city":"南宁",
                                    "sch_name":"南宁二中",
                                    "name":"2010-2011学年广西南宁二中高三（上）10月月考数学试卷（文科）",
                                    "region":"广西",
                                    "year":2011,
                                    "category":"月考试卷",
                                    "id":2418801663
                                },
                                {
                                    "province":"广西",
                                    "city":"南宁",
                                    "sch_name":"南宁二中",
                                    "name":"2010-2011学年广西南宁二中高三（上）10月月考数学试卷（理科）",
                                    "region":"广西",
                                    "year":2011,
                                    "category":"月考试卷",
                                    "id":2806250751
                                },
                                {
                                    "province":"湖北",
                                    "city":"十堰",
                                    "sch_name":"",
                                    "name":"2009-2010学年湖北省十堰一中高三（上）10月调考数学试卷（理科）",
                                    "region":"湖北",
                                    "year":2010,
                                    "category":"月考试卷",
                                    "id":3365927935
                                },
                                {
                                    "province":"湖北",
                                    "city":"宜昌",
                                    "sch_name":"宜昌一中",
                                    "name":"2008-2009学年湖北省宜昌一中高三（上）12月月考数学试卷（文科）",
                                    "region":"湖北",
                                    "year":2009,
                                    "category":"月考试卷",
                                    "id":2602957823
                                },
                                {
                                    "province":"山东",
                                    "city":"青岛",
                                    "sch_name":"",
                                    "name":"2008-2009学年山东省青岛市高三（上）期中数学试卷（理科）",
                                    "region":"山东",
                                    "year":2009,
                                    "category":"期中试卷",
                                    "id":119930623
                                },
                                {
                                    "province":"山东",
                                    "city":"青岛",
                                    "sch_name":"",
                                    "name":"2008-2009学年山东省青岛市高三（上）期中数学试卷（文科）",
                                    "region":"山东",
                                    "year":2009,
                                    "category":"期中试卷",
                                    "id":106495743
                                }
                            ],
                            "blocks":{
                                "stems":[
                                    {
                                        "stem":"定义${A-B= \{x\mathrel{|} x\in A且x\notin B\}}$，若${M= \{1,\, 2,\, 3,\, 4,\, 5\}}$，${N= \{2,\, 3,\, 6\}}$，则${N-M= (}$　　${)}$",
                                        "options":{
                                            "A":"${M}$",
                                            "B":"${N}$",
                                            "C":"${\{1,\, 4,\, 5\}}$",
                                            "D":"${\{6\}}$"
                                        }
                                    }
                                ],
                                "types":[
                                    "选择题"
                                ],
                                "solutions":[
                                    "解：∵${{{{{{A-B= \{x\mathrel{|} x∈ A且x∉ B\}}}}}}}$，<br>∴${{{{{{N-M= \{x\mathrel{|} x∈ N且x∉ M\}}}}}}}$.<br>又∵${{{{{{M= \{1,\, 2,\, 3,\, 4,\, 5\}}}}}}}$，${{{{{{N= \{2,\, 3,\, 6\}}}}}}}$，<br>∴${{{N-M={ \{6\} }}}}$.<br>故选：${\rm D}$."
                                ],
                                "explanations":[
                                    "利用新定义，欲求集合${N-M}$，即找属于${N}$但不属于${M}$的元素组成的集合，由已知集合${M}$，${N}$即可求得${N-M}$．"
                                ],
                                "answers":[
                                    "D"
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "chance":0.0058,
                                            "score":0.03
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ]
                                ]
                            },
                            "description":"",
                            "type":"选择题",
                            "period":"高中",
                            "difficulty":3,
                            "refer_times":15,
                            "knowledges":[
                                {
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "chance":0.0058,
                                    "score":0.03,
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                }
                            ],
                            "subject":"数学",
                            "elite":1,
                            "core_knowledges":[

                            ],
                            "id":3878217983,
                            "score":3
                        }
                    ]
                }
            ]
        },
        {
            "title":"卷II（非选择题）",
            "note":"",
            "blocks":[
                {
                    "title":"填空题（本大题共计2小题，每题3分，共计6分）",
                    "note":"",
                    "type":"填空题",
                    "default_score":3,
                    "questions":[
                        {
                            "comment":"本题考查学生对新定义的题型的理解和把握程度，弄准集合中元素的构造方式，考查列举法写集合，分类讨论思想．",
                            "refer_exampapers":[
                                {
                                    "province":"宁夏",
                                    "city":"石嘴山",
                                    "sch_name":"",
                                    "name":"2015-2016学年宁夏石嘴山三中高一（上）第一次月考数学试卷",
                                    "region":"宁夏",
                                    "year":2016,
                                    "category":"月考试卷",
                                    "id":913177343
                                },
                                {
                                    "province":"",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2011年《龙门亮剑》高三数学（文科）一轮复习：第1章第1节（人教AB通用）",
                                    "region":"",
                                    "year":2011,
                                    "category":"高考复习",
                                    "id":3719757567
                                },
                                {
                                    "province":"",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2011年《龙门亮剑》高三数学（理科）一轮复习：第1篇第1节（北师大版）",
                                    "region":"",
                                    "year":2011,
                                    "category":"高考复习",
                                    "id":3694460671
                                },
                                {
                                    "province":"江苏",
                                    "city":"扬州",
                                    "sch_name":"",
                                    "name":"2010-2011学年江苏省扬州市宝应县曹甸高级中学高一（上）数学试卷（必修1）",
                                    "region":"江苏",
                                    "year":2011,
                                    "category":"期末试卷",
                                    "id":1013972223
                                }
                            ],
                            "blocks":{
                                "types":[
                                    "填空题"
                                ],
                                "explanations":[
                                    "利用集合中新定义的元素的属性得出集合中元素的构成是解决该问题的关键，集合中元素不多时，将各个元素列举出来从而得到所求的集合．"
                                ],
                                "solutions":[
                                    "解：当${x= 0}$，${y= 2}$时，${z_{1}= 0}$；<br/>当${x= 0}$，${y= 3}$时，${z_{2}= 0}$；<br/>当${x= 1}$，${y= 2}$时，${z_{3}= 1\times 2\times (1+ 2)= 6}$；<br/>当${x= 1}$，${y= 3}$时，${z_{4}= 1\times 3\times (1+ 3)= 12}$，<br/>∴${A\odot B= \{0,\, 6,\, 12\}}$．<br/>故答案为：${\{0,\, 6,\, 12\}}$．"
                                ],
                                "answers":[
                                    [
                                        "${\{0,\, 6,\, 12\}}$"
                                    ]
                                ],
                                "stems":[
                                    {
                                        "stem":"定义集合运算${A\odot B= \{z\mathrel{|} z= xy(x+ y),\, x\in A,\, y\in B\}}$，设集合${A= \{0,\, 1\}}$，${B= \{2,\, 3\}}$，则集合${A\odot B= }$________"
                                    }
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义"
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ]
                                ]
                            },
                            "description":"",
                            "type":"填空题",
                            "period":"高中",
                            "difficulty":4,
                            "refer_times":4,
                            "knowledges":[
                                {
                                    "chance":0.0058,
                                    "score":0.03,
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                }
                            ],
                            "subject":"数学",
                            "elite":1,
                            "core_knowledges":[

                            ],
                            "id":3207981311,
                            "score":3
                        },
                        {
                            "comment":"本题考查学生对新定义题型的理解和把握能力，理解数域的定义是解决该题的关键．考查学生的构造性思维．",
                            "refer_exampapers":[
                                {
                                    "province":"福建",
                                    "city":"漳州",
                                    "sch_name":"",
                                    "name":"2014-2015学年福建省漳州市长泰一中高一（上）期中数学试卷",
                                    "region":"福建",
                                    "year":2015,
                                    "category":"期中试卷",
                                    "id":4266065663
                                },
                                {
                                    "province":"辽宁",
                                    "city":"沈阳",
                                    "sch_name":"沈阳二中",
                                    "name":"2013-2014学年辽宁省沈阳二中高一（上）10月段考数学试卷",
                                    "region":"辽宁",
                                    "year":2014,
                                    "category":"月考试卷",
                                    "id":3122527487
                                },
                                {
                                    "province":"天津",
                                    "city":"",
                                    "sch_name":"天津一中",
                                    "name":"2013-2014学年天津一中高一（上）第一次月考数学试卷",
                                    "region":"天津",
                                    "year":2014,
                                    "category":"月考试卷",
                                    "id":3874487295
                                },
                                {
                                    "province":"福建",
                                    "city":"三明",
                                    "sch_name":"",
                                    "name":"2013-2014学年福建省三明市宁化二中高三（上）期中数学试卷（理科）",
                                    "region":"福建",
                                    "year":2014,
                                    "category":"期中试卷",
                                    "id":112459519
                                },
                                {
                                    "province":"",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2013年高考数学复习卷E（十三）",
                                    "region":"",
                                    "year":2013,
                                    "category":"高考复习",
                                    "id":986578175
                                },
                                {
                                    "province":"浙江",
                                    "city":"杭州",
                                    "sch_name":"",
                                    "name":"2012-2013学年浙江省杭州市西湖高级中学高一（上）10月月考数学试卷",
                                    "region":"浙江",
                                    "year":2013,
                                    "category":"月考试卷",
                                    "id":3200121855
                                },
                                {
                                    "province":"青海",
                                    "city":"",
                                    "sch_name":"湟川中学",
                                    "name":"2011-2012学年青海省湟川中学高三（上）第二次月考数学试卷",
                                    "region":"青海",
                                    "year":2012,
                                    "category":"月考试卷",
                                    "id":1805122303
                                },
                                {
                                    "province":"上海",
                                    "city":"浦东新",
                                    "sch_name":"建平中学",
                                    "name":"2009-2010学年上海市浦东新区建平中学高三（上）摸底数学试卷（理科）",
                                    "region":"上海",
                                    "year":2010,
                                    "category":"高考模拟",
                                    "id":2959670527
                                },
                                {
                                    "province":"江苏",
                                    "city":"南通",
                                    "sch_name":"启东中学",
                                    "name":"2008-2009学年江苏省南通市启东中学高三（上）段考数学试卷（理科）",
                                    "region":"江苏",
                                    "year":2009,
                                    "category":"月考试卷",
                                    "id":3880975359
                                },
                                {
                                    "province":"福建",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2008年福建省高考数学试卷（理科）",
                                    "region":"福建",
                                    "year":2008,
                                    "category":"高考真卷",
                                    "id":4158193407
                                },
                                {
                                    "province":"广东",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"广东省高考数学一轮复习：1.3 四种命题及其关系",
                                    "region":"广东",
                                    "year":0,
                                    "category":"高考复习",
                                    "id":3716218623
                                }
                            ],
                            "blocks":{
                                "answers":[
                                    [
                                        "③④"
                                    ]
                                ],
                                "explanations":[
                                    "利用已知条件中数域的定义判断各命题的真假，关键把握数域是对加减乘除四则运算封闭．"
                                ],
                                "solutions":[
                                    "解：要满足对四种运算的封闭，只有一个个来检验，如①对除法如${ \dfrac{1}{2}\notin Z}$不满足，所以排除；<br>对②当有理数集${Q}$中多一个元素${i}$则会出现${1+ i\notin }$该集合，所以它也不是一个数域；③④成立．<br>故答案为：③④．"
                                ],
                                "types":[
                                    "填空题"
                                ],
                                "stems":[
                                    {
                                        "options":{

                                        },
                                        "stem":"设${P}$是一个数集，且至少含有两个数，若对任意${a}$、${b\in P}$，都有${a+ b}$、${a-b}$，${ab}$、${ \dfrac{a}{b}\in P}$（除数${b\neq 0}$），则称${P}$是一个数域．例如有理数集${Q}$是数域；数集${F= \{a+ b \sqrt{2}\mathrel{|} a,\, b\in Q\}}$也是数域．有下列命题：<br>①整数集是数域；<br>②若有理数集${Q\subseteq M}$，则数集${M}$必为数域；<br>③数域必为无限集；<br>④存在无穷多个数域．<br>其中正确的命题的序号是________．（把你认为正确的命题的序号填填上）"
                                    }
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        },
                                        {
                                            "importance":1,
                                            "chance":0,
                                            "score":0,
                                            "id":2126118911,
                                            "name":"四种命题的真假关系",
                                            "videos":[

                                            ]
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ]
                                ]
                            },
                            "description":"",
                            "type":"填空题",
                            "period":"高中",
                            "difficulty":5,
                            "refer_times":11,
                            "knowledges":[
                                {
                                    "importance":1,
                                    "chance":0.0058,
                                    "score":0.03,
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                },
                                {
                                    "importance":1,
                                    "chance":0,
                                    "score":0,
                                    "id":2126118911,
                                    "name":"四种命题的真假关系",
                                    "videos":[

                                    ]
                                }
                            ],
                            "subject":"数学",
                            "id":2888755711,
                            "score":3
                        }
                    ]
                },
                {
                    "title":"解答题（本大题共计3小题，每题10分，共计30分）",
                    "note":"",
                    "type":"解答题",
                    "default_score":10,
                    "questions":[
                        {
                            "comment":"本题主要考查集合中元素的确定性、互异性、无序性，属于基础题．",
                            "refer_exampapers":[
                                {
                                    "province":"江苏",
                                    "city":"徐州",
                                    "sch_name":"",
                                    "name":"2014-2015学年江苏省徐州市新沂市王楼中学高一（上）第一次月考数学试卷",
                                    "region":"江苏",
                                    "year":2015,
                                    "category":"月考试卷",
                                    "id":3875535871
                                },
                                {
                                    "province":"江苏",
                                    "city":"宿迁",
                                    "sch_name":"",
                                    "name":"2013-2014学年江苏省宿迁市高一（上）第一次月考数学试卷（普通班）",
                                    "region":"江苏",
                                    "year":2014,
                                    "category":"月考试卷",
                                    "id":2638871551
                                }
                            ],
                            "blocks":{
                                "types":[
                                    "解答题",
                                    "解答题",
                                    "解答题",
                                    "解答题"
                                ],
                                "explanations":[
                                    "由于选项<span class='tiku-list-nr'>${(1)(2)(3)}$</span>中的对象不满足元素的确定性，故<span class='tiku-list-nr'>${(1)(2)(3)}$</span>中的对象不能构成集合．由于<span class='tiku-list-nr'>${(4)}$</span>中的对象满足元素的确定性和互异性，故<span class='tiku-list-nr'>${(4)}$</span>中的对象能构成集合．",
                                    "",
                                    "",
                                    ""
                                ],
                                "solutions":[
                                    "解：由于“高个子”没有确定的标准，故<span class='tiku-list-nr'>${(1)}$</span>中的对象不满足元素的确定性，故<span class='tiku-list-nr'>${(1)}$</span>中的对象不能构成集合．<br/>由于“著名”没有确定的标准，故",
                                    "<span class='tiku-list-nr'>${(2)}$</span>中的对象不满足元素的确定性，故<span class='tiku-list-nr'>${(2)}$</span>中的对象不能构成集合．．<br/>由于“很大”没有明确的标准，故",
                                    "<span class='tiku-list-nr'>${(3)}$</span>中的对象不满足元素的确定性，故<span class='tiku-list-nr'>${(3)}$</span>中的对象不能构成集合．<br/>由于“倒数等于它自身的实数”是确定的，故",
                                    "<span class='tiku-list-nr'>${(4)}$</span>中的对象满足元素的确定性和互异性，故<span class='tiku-list-nr'>${(4)}$</span>中的对象能构成集合．<br/>"
                                ],
                                "answers":[
                                    "<span class='tiku-list-nr'>${(4)}$</span>",
                                    "",
                                    "",
                                    ""
                                ],
                                "stems":[
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(1)}$</span>某班所有高个子的学生 "
                                    },
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(2)}$</span>著名的艺术家"
                                    },
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(3)}$</span>一本很大的书 "
                                    },
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(4)}$</span>倒数等于它自身的实数．"
                                    }
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        }
                                    ],
                                    [
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        }
                                    ],
                                    [
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        }
                                    ],
                                    [
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ],
                                    [

                                    ],
                                    [

                                    ],
                                    [

                                    ]
                                ]
                            },
                            "description":"下列四组对象，能构成集合的是________（填序号）",
                            "type":"解答题",
                            "period":"高中",
                            "difficulty":2,
                            "refer_times":2,
                            "knowledges":[
                                {
                                    "importance":1,
                                    "chance":0.0058,
                                    "score":0.03,
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                }
                            ],
                            "subject":"数学",
                            "id":89581823,
                            "score":10
                        },
                        {
                            "comment":"本题主要考查二倍角公式、两角和与差的正弦公式的应用和正弦函数的基本性质．三角函数是高考的重点，每年必考，要强化复习．",
                            "refer_exampapers":[
                                {
                                    "province":"北京",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2013-2014学年北京市民大附中高三（上）12月月考数学试卷（理科）",
                                    "region":"北京",
                                    "year":2014,
                                    "category":"月考试卷",
                                    "id":1838414591
                                },
                                {
                                    "province":"广东",
                                    "city":"东莞",
                                    "sch_name":"",
                                    "name":"2013-2014学年广东省北师大东莞石竹附中高三（上）12月月考数学试卷（理科）",
                                    "region":"广东",
                                    "year":2014,
                                    "category":"月考试卷",
                                    "id":2567764991
                                },
                                {
                                    "province":"四川",
                                    "city":"眉山",
                                    "sch_name":"",
                                    "name":"2013-2014学年四川省眉山市仁寿一中南校区高一（下）3月月考数学试卷（理科）",
                                    "region":"四川",
                                    "year":2014,
                                    "category":"月考试卷",
                                    "id":3439721471
                                },
                                {
                                    "province":"江西",
                                    "city":"上饶",
                                    "sch_name":"",
                                    "name":"2011-2012学年江西省上饶市横峰中学高二（下）期中数学试卷（理科）",
                                    "region":"江西",
                                    "year":2012,
                                    "category":"期中试卷",
                                    "id":205651711
                                },
                                {
                                    "province":"北京",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2011-2012学年北京62中高三（上）9月月考数学试卷（理科）",
                                    "region":"北京",
                                    "year":2012,
                                    "category":"月考试卷",
                                    "id":3235511551
                                },
                                {
                                    "province":"河南",
                                    "city":"周口",
                                    "sch_name":"",
                                    "name":"2011年河南省周口市项城三中高三第一次摸底数学试卷（文科）",
                                    "region":"河南",
                                    "year":2011,
                                    "category":"高考模拟",
                                    "id":3315269119
                                },
                                {
                                    "province":"陕西",
                                    "city":"宝鸡",
                                    "sch_name":"",
                                    "name":"2011年陕西省宝鸡市扶风县高考数学模拟试卷（理科）",
                                    "region":"陕西",
                                    "year":2011,
                                    "category":"高考模拟",
                                    "id":3987734271
                                },
                                {
                                    "province":"湖南",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2010年湖南省高考数学试卷（理科）",
                                    "region":"湖南",
                                    "year":2010,
                                    "category":"高考真卷",
                                    "id":4169203455
                                },
                                {
                                    "province":"",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"2010年高考数学试卷精编：4.3 三角函数的图象和性质",
                                    "region":"",
                                    "year":2010,
                                    "category":"高考复习",
                                    "id":4157800191
                                },
                                {
                                    "province":"",
                                    "city":"",
                                    "sch_name":"",
                                    "name":"3年高考2年模拟：4.2 三角函数的图象和性质及三角恒等变换（1）",
                                    "region":"",
                                    "year":0,
                                    "category":"高考模拟",
                                    "id":3384409087
                                }
                            ],
                            "blocks":{
                                "answers":[
                                    "解：<span class='tiku-list-nr'>${(1)}$</span>∵${f(x)= \sqrt{3}\sin 2x-2\sin ^{2}x= \sqrt{3}\sin 2x+ \cos 2x-1= 2\sin (2x+ \dfrac{\pi }{6})-1}$<br/>故函数${f(x)}$的最大值等于${2-1= 1}$",
                                    "<span class='tiku-list-nr'>${(2)}$</span>由${f(x)= 0}$得${2\sqrt{3}\sin \, x\cos \, x= 2\sin ^{2}x}$，于是${\sin \, x= 0}$，或${\sqrt{3}\cos \, x= \sin \, x}$即${\tan \, x= \sqrt{3}}$<br/>由${\sin \, x= 0}$可知${x= k\pi }$；<br/>由${\tan \, x= \sqrt{3}}$可知${x= k\pi + \dfrac{\pi }{3}}$．<br/>故函数${f(x)}$的零点的集合为${\{x\mathrel{|} x= k\pi 或x= k\pi + \dfrac{\pi }{3},\, k\in Z\}}$"
                                ],
                                "explanations":[
                                    "<span class='tiku-list-nr'>${(1)}$</span>先根据二倍角公式和两角和与差的公式进行化简，再由正弦函数的最值可得到答案．",
                                    "<span class='tiku-list-nr'>${(2)}$</span>令${f(x)= 0}$可得到${2\sqrt{3}\sin \, x\cos \, x= 2\sin ^{2}x}$，进而可得到${\sin \, x= 0}$或${\tan \, x= \sqrt{3}}$，即可求出对应的${x}$的取值集合，得到答案．"
                                ],
                                "solutions":[
                                    "解：<span class='tiku-list-nr'>${(1)}$</span>∵${f(x)= \sqrt{3}\sin 2x-2\sin ^{2}x= \sqrt{3}\sin 2x+ \cos 2x-1= 2\sin (2x+ \dfrac{\pi }{6})-1}$<br/>故函数${f(x)}$的最大值等于${2-1= 1}$",
                                    "<span class='tiku-list-nr'>${(2)}$</span>由${f(x)= 0}$得${2\sqrt{3}\sin \, x\cos \, x= 2\sin ^{2}x}$，于是${\sin \, x= 0}$，或${\sqrt{3}\cos \, x= \sin \, x}$即${\tan \, x= \sqrt{3}}$<br/>由${\sin \, x= 0}$可知${x= k\pi }$；<br/>由${\tan \, x= \sqrt{3}}$可知${x= k\pi + \dfrac{\pi }{3}}$．<br/>故函数${f(x)}$的零点的集合为${\{x\mathrel{|} x= k\pi 或x= k\pi + \dfrac{\pi }{3},\, k\in Z\}}$"
                                ],
                                "stems":[
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(1)}$</span>求函数${f(x)}$的最大值；"
                                    },
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(2)}$</span>求函数${f(x)}$的零点的集合．"
                                    }
                                ],
                                "types":[
                                    "解答题",
                                    "解答题"
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "importance":3,
                                            "chance":0.0355,
                                            "score":0.16,
                                            "id":2102919167,
                                            "name":"三角函数的最值",
                                            "videos":[

                                            ]
                                        },
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        },
                                        {
                                            "importance":5,
                                            "chance":0.1065,
                                            "score":0.91,
                                            "id":2142437375,
                                            "name":"函数的零点",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1903034367,
                                                    "name":"函数的零点"
                                                },
                                                {
                                                    "from":"suoluo",
                                                    "id":1902968831,
                                                    "name":"函数零点存在性的判定"
                                                }
                                            ]
                                        }
                                    ],
                                    [
                                        {
                                            "importance":3,
                                            "chance":0.0355,
                                            "score":0.16,
                                            "id":2102919167,
                                            "name":"三角函数的最值",
                                            "videos":[

                                            ]
                                        },
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        },
                                        {
                                            "importance":5,
                                            "chance":0.1065,
                                            "score":0.91,
                                            "id":2142437375,
                                            "name":"函数的零点",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1903034367,
                                                    "name":"函数的零点"
                                                },
                                                {
                                                    "from":"suoluo",
                                                    "id":1902968831,
                                                    "name":"函数零点存在性的判定"
                                                }
                                            ]
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ],
                                    [

                                    ]
                                ]
                            },
                            "description":"已知函数${f(x)= \sqrt{3}\sin 2x-2\sin ^{2}x}$．",
                            "type":"解答题",
                            "period":"高中",
                            "difficulty":3,
                            "refer_times":10,
                            "knowledges":[
                                {
                                    "importance":3,
                                    "chance":0.0355,
                                    "score":0.16,
                                    "id":2102919167,
                                    "name":"三角函数的最值",
                                    "videos":[

                                    ]
                                },
                                {
                                    "importance":1,
                                    "chance":0.0058,
                                    "score":0.03,
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                },
                                {
                                    "importance":5,
                                    "chance":0.1065,
                                    "score":0.91,
                                    "id":2142437375,
                                    "name":"函数的零点",
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1903034367,
                                            "name":"函数的零点"
                                        },
                                        {
                                            "from":"suoluo",
                                            "id":1902968831,
                                            "name":"函数零点存在性的判定"
                                        }
                                    ]
                                }
                            ],
                            "subject":"数学",
                            "id":755231487,
                            "score":10
                        },
                        {
                            "comment":"本题考查了三解函数及解三角形知识的综合应用，难度较大，关键是通过构造三角形利用正余弦定理构建三角函数模型．",
                            "refer_exampapers":[
                                {
                                    "province":"江苏",
                                    "city":"泰州",
                                    "sch_name":"",
                                    "name":"2014-2015学年江苏省泰州市兴化市文正实验学校高三（上）第一次月考数学试卷（理科）",
                                    "region":"江苏",
                                    "year":2015,
                                    "category":"月考试卷",
                                    "id":2949381375
                                },
                                {
                                    "province":"江苏",
                                    "city":"淮安",
                                    "sch_name":"",
                                    "name":"2013-2014学年江苏省淮安市淮海中学高三（下）期初数学试卷",
                                    "region":"江苏",
                                    "year":2014,
                                    "category":"高考模拟",
                                    "id":4283235327
                                },
                                {
                                    "province":"江苏",
                                    "city":"泰州",
                                    "sch_name":"",
                                    "name":"2013-2014学年江苏省泰州市高三（上）期末数学试卷",
                                    "region":"江苏",
                                    "year":2014,
                                    "category":"期末试卷",
                                    "id":4211736319
                                }
                            ],
                            "blocks":{
                                "types":[
                                    "解答题",
                                    "解答题"
                                ],
                                "explanations":[
                                    "第<span class='tiku-list-nr'>${(1)}$</span>问，时间${t}$分成两段，从${D}$到${C}$设为${t_{1}}$，从${C}$到${A}$设为${t_{2}}$，要建立${t}$与${\theta }$的函数关系，需要构造三角形，利用正余弦定理解决．第",
                                    "<span class='tiku-list-nr'>${(2)}$</span>问，根据第<span class='tiku-list-nr'>${(1)}$</span>问三角函数的形式，当${\theta = \dfrac{\pi }{2}}$时，${t}$取最小值．"
                                ],
                                "solutions":[
                                    "<img src='http://yx-kbs-ks3.haofenshu.com/images/b76ceda83f793d7457f8fad711f0e4b5.png@w=204&h=194' alt='go题库' style='vertical-align:middle;FLOAT:right;'/>解：<span class='tiku-list-nr'>${(1)}$</span>如图，连接${AD}$，在${\triangle ACD}$中，${AB= BD= l}$，${\angle B= \dfrac{\pi }{3}}$，<br/>∴${AD= l}$，${\angle A= \dfrac{\pi }{3}}$，<br/>∵货物从${D}$处至${C}$处运行速度为${v}$，设运行的时间为${t_{1}}$，则${CD= vt_{1}}$，<br/> 货物从${C}$处至${A}$处运行速度为${3v}$，设运行的时间为${t_{2}}$，则${AC= 3vt_{2}}$，<br/>∴在${\triangle ACD}$中，由正弦定理得，${\dfrac{vt_{1}}{\sin A}= \dfrac{l}{\sin (\pi -\theta )}}$，${\dfrac{3vt_{2}}{\sin (\theta -\dfrac{\pi }{3})}= \dfrac{l}{\sin (\pi -\theta )}}$ <br/>∴${t_{1}= \dfrac{\sqrt{3}l}{2v\sin \theta }}$，${t_{2}= \dfrac{l\sin (\theta -\dfrac{\pi }{3})}{3v\sin \theta }}$<br/>∴${t= t_{1}+ t_{2}= \dfrac{\sqrt{3}l}{2v\sin \theta }+ \dfrac{l\sin (\theta -\dfrac{\pi }{3})}{3v\sin \theta }}$<br/>${= \dfrac{3\sqrt{3}l+ 2l\sin (\theta -\dfrac{\pi }{3})}{6v\sin \theta }}$，${(\dfrac{\pi }{3}\lt \theta \lt \dfrac{2\pi }{3})}$；",
                                    "<span class='tiku-list-nr'>${(2)}$</span>由<span class='tiku-list-nr'>${(1)}$</span>知当${\theta = \dfrac{\pi }{2}}$，${t}$最小，即${C}$在${AB}$的中点时，${t}$取最小值．"
                                ],
                                "answers":[
                                    "<img src='http://yx-kbs-ks3.haofenshu.com/images/b76ceda83f793d7457f8fad711f0e4b5.png@w=204&h=194' alt='go题库' style='vertical-align:middle;FLOAT:right;'/>解：<span class='tiku-list-nr'>${(1)}$</span>如图，连接${AD}$，在${\triangle ACD}$中，${AB= BD= l}$，${\angle B= \dfrac{\pi }{3}}$，<br/>∴${AD= l}$，${\angle A= \dfrac{\pi }{3}}$，<br/>∵货物从${D}$处至${C}$处运行速度为${v}$，设运行的时间为${t_{1}}$，则${CD= vt_{1}}$，<br/> 货物从${C}$处至${A}$处运行速度为${3v}$，设运行的时间为${t_{2}}$，则${AC= 3vt_{2}}$，<br/>∴在${\triangle ACD}$中，由正弦定理得，${\dfrac{vt_{1}}{\sin A}= \dfrac{l}{\sin (\pi -\theta )}}$，${\dfrac{3vt_{2}}{\sin (\theta -\dfrac{\pi }{3})}= \dfrac{l}{\sin (\pi -\theta )}}$ <br/>∴${t_{1}= \dfrac{\sqrt{3}l}{2v\sin \theta }}$，${t_{2}= \dfrac{l\sin (\theta -\dfrac{\pi }{3})}{3v\sin \theta }}$<br/>∴${t= t_{1}+ t_{2}= \dfrac{\sqrt{3}l}{2v\sin \theta }+ \dfrac{l\sin (\theta -\dfrac{\pi }{3})}{3v\sin \theta }}$<br/>${= \dfrac{3\sqrt{3}l+ 2l\sin (\theta -\dfrac{\pi }{3})}{6v\sin \theta }}$，${(\dfrac{\pi }{3}\lt \theta \lt \dfrac{2\pi }{3})}$；",
                                    "<span class='tiku-list-nr'>${(2)}$</span>由<span class='tiku-list-nr'>${(1)}$</span>知当${\theta = \dfrac{\pi }{2}}$，${t}$最小，即${C}$在${AB}$的中点时，${t}$取最小值．"
                                ],
                                "stems":[
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(1)}$</span>当${\theta }$变化时，试将货物运行的时间${t}$表示成${\theta }$的函数（用含有${v}$和${l}$的式子）；"
                                    },
                                    {
                                        "stem":"<span class='tiku-list-nr'>${(2)}$</span>当${t}$最小时，${C}$点应设计在${AB}$的什么位置？"
                                    }
                                ],
                                "knowledges":[
                                    [
                                        {
                                            "importance":1,
                                            "chance":0,
                                            "score":0,
                                            "id":2131492863,
                                            "name":"已知三角函数模型的应用问题",
                                            "videos":[

                                            ]
                                        },
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        },
                                        {
                                            "importance":3,
                                            "chance":0.0533,
                                            "score":0.43,
                                            "id":2145845247,
                                            "name":"函数解析式的求解及常用方法",
                                            "videos":[

                                            ]
                                        },
                                        {
                                            "importance":3,
                                            "chance":0.0355,
                                            "score":0.16,
                                            "id":2102919167,
                                            "name":"三角函数的最值",
                                            "videos":[

                                            ]
                                        }
                                    ],
                                    [
                                        {
                                            "importance":1,
                                            "chance":0,
                                            "score":0,
                                            "id":2131492863,
                                            "name":"已知三角函数模型的应用问题",
                                            "videos":[

                                            ]
                                        },
                                        {
                                            "importance":1,
                                            "chance":0.0058,
                                            "score":0.03,
                                            "id":2147418111,
                                            "name":"集合的含义",
                                            "videos":[
                                                {
                                                    "from":"suoluo",
                                                    "id":1904541695,
                                                    "name":"集合的概念"
                                                }
                                            ]
                                        },
                                        {
                                            "importance":3,
                                            "chance":0.0533,
                                            "score":0.43,
                                            "id":2145845247,
                                            "name":"函数解析式的求解及常用方法",
                                            "videos":[

                                            ]
                                        },
                                        {
                                            "importance":3,
                                            "chance":0.0355,
                                            "score":0.16,
                                            "id":2102919167,
                                            "name":"三角函数的最值",
                                            "videos":[

                                            ]
                                        }
                                    ]
                                ],
                                "core_knowledges":[
                                    [

                                    ],
                                    [

                                    ]
                                ]
                            },
                            "description":"<img src='http://yx-kbs-ks3.haofenshu.com/images/ed642e2c6ce01b770f0aa688d76330cf.png@w=196&h=169' alt='go题库' style='vertical-align:middle;FLOAT:right;'/>某运输装置如图所示，其中钢结构${ABD}$是${AB= BD= l}$，${\angle B= \dfrac{\pi }{3}}$的固定装置，${AB}$上可滑动的点${C}$使${CD}$垂直与底面（${C}$不${A}$，${B}$与重合），且${CD}$可伸缩（当${CD}$伸缩时，装置${ABD}$随之绕${D}$在同一平面内旋转），利用该运输装置可以将货物从地面${D}$处沿${D\rightarrow C\rightarrow A}$运送至${A}$处，货物从${D}$处至${C}$处运行速度为${v}$，从${C}$处至${A}$处运行速度为${3v}$．为了使运送货物的时间${t}$最短，需在运送前调整运输装置中${\angle DCB= \theta }$的大小．",
                            "type":"解答题",
                            "period":"高中",
                            "difficulty":4,
                            "refer_times":3,
                            "knowledges":[
                                {
                                    "importance":1,
                                    "chance":0,
                                    "score":0,
                                    "id":2131492863,
                                    "name":"已知三角函数模型的应用问题",
                                    "videos":[

                                    ]
                                },
                                {
                                    "importance":1,
                                    "chance":0.0058,
                                    "score":0.03,
                                    "id":2147418111,
                                    "name":"集合的含义",
                                    "videos":[
                                        {
                                            "from":"suoluo",
                                            "id":1904541695,
                                            "name":"集合的概念"
                                        }
                                    ]
                                },
                                {
                                    "importance":3,
                                    "chance":0.0533,
                                    "score":0.43,
                                    "id":2145845247,
                                    "name":"函数解析式的求解及常用方法",
                                    "videos":[

                                    ]
                                },
                                {
                                    "importance":3,
                                    "chance":0.0355,
                                    "score":0.16,
                                    "id":2102919167,
                                    "name":"三角函数的最值",
                                    "videos":[

                                    ]
                                }
                            ],
                            "subject":"数学",
                            "id":120121599,
                            "score":10
                        }
                    ]
                }
            ]
        }
    ]
  },
  mounted(){
    console.log(this.volumes)
   MathJax.Hub.Config({
      tex2jax: {
          inlineMath: [["$", "$"]]
      },
      "HTML-CSS": {linebreaks: {automatic: true}, matchFontHeight: false},
      SVG: {linebreaks: {automatic: true}, matchFontHeight: false}
  });
  MathJax.Hub.Configured();
  MathJax.Hub.Queue(["Typeset", MathJax.Hub, function () {
      var question_options = document.getElementsByClassName('question-options');
      for (var ix in question_options) {
          var question_option = question_options[ix];
          try {
              question_option.setAttribute('class', question_option.className.replace(/ul-\d/g, ''));
          } catch (err) {
          }
          var choice_options = question_option.childNodes;
          var maxWidth = 0;
          var boxWidth = question_option.offsetWidth;
          for (var co in choice_options) {

              if (isNaN(co))
                  continue;

              choice_options[co].setAttribute('data-width', choice_options[co].offsetWidth);
              if (choice_options[co].offsetWidth > maxWidth)
                  maxWidth = choice_options[co].offsetWidth;
          }

          try {
              if (maxWidth > boxWidth * 0.44) {
                  question_option.setAttribute('class', [question_option.className, 'ul-1'].join(' '));
              } else if (maxWidth > boxWidth * 0.21) {
                  question_option.setAttribute('class', [question_option.className, 'ul-2'].join(' '));
              } else {
                  question_option.setAttribute('class', [question_option.className, 'ul-4'].join(' '));
              }
          } catch (err) {

          }
      }
  }]);
  },
  updated(){
    console.log(this.volumes)

    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [["$", "$"]]
        },
        "HTML-CSS": {linebreaks: {automatic: true}, matchFontHeight: false},
        SVG: {linebreaks: {automatic: true}, matchFontHeight: false}
    });
    MathJax.Hub.Configured();
    MathJax.Hub.Queue(["Typeset", MathJax.Hub, function () {

        var question_options = document.getElementsByClassName('question-options');
        for (var ix in question_options) {
            var question_option = question_options[ix];
            try {
                question_option.setAttribute('class', question_option.className.replace(/ul-\d/g, ''));
            } catch (err) {
            }

            var choice_options = question_option.childNodes;
            var maxWidth = 0;
            var boxWidth = question_option.offsetWidth;
            for (var co in choice_options) {

                if (isNaN(co))
                    continue;

                choice_options[co].setAttribute('data-width', choice_options[co].offsetWidth);
                if (choice_options[co].offsetWidth > maxWidth)
                    maxWidth = choice_options[co].offsetWidth;
            }

            try {

                if (maxWidth > boxWidth * 0.44) {
                    question_option.setAttribute('class', [question_option.className, 'ul-1'].join(' '));
                } else if (maxWidth > boxWidth * 0.21) {
                    question_option.setAttribute('class', [question_option.className, 'ul-2'].join(' '));
                } else {
                    question_option.setAttribute('class', [question_option.className, 'ul-4'].join(' '));
                }
            } catch (err) {

            }
        }
    }]);
  },
  methods: {
    
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
