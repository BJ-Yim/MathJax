<template>
  <div id="app">
    <div>定义${A-B= \{x\mathrel{|} x\in A且x\notin B\}}$，若${M= \{1,\, 2,\, 3,\, 4,\, 5\}}$，${N= \{2,\, 3,\, 6\}}$，则${N-M= (}$　　${)}$</div>
    
    <span>{{tex}}</span>
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
import axios from 'axios';
export default {
  name: 'App',
  data () {
    return {
      tex: "",
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
    axios.get('http://172.31.0.199:8113/mock/11/api/mathjax')
    .then( (response) => {
        console.log(response)
        this.volumes = response.data.data.volumes;
        console.log(this.volumes)
        this.tex = this.volumes[1]['blocks'][0]['questions'][0]['blocks']['stems'][0]['stem'];
    })
    .catch(function (error) {
        console.log(error);
    });
  },
  mounted(){
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ["$", "$"], ["\\\\(","\\\\)"] ]
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
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ["$", "$"], ["\\\\(","\\\\)"] ]
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
