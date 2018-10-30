<template>
	<div :id="questionId" :detail="false" :hideRefer="hideRefer" ref="question.id" class="question" v-if="question && question.blocks">
		<div class="question-anchor" :id="anchor">&nbsp;</div>
		<span class="question-info" v-if="question.description">
			<span class="question-number" v-if="questionNr">{{ questionNr }}.</span><a class="refer-info" v-if="refer && !hideRefer" target="__blank" :href="paper">（{{ refer }}）</a><span class="question-score" v-if="showScore" style="color: #999">({{ question.score }}分) </span>
		</span>
		<span class="description kb_question-content" v-if="question.description" v-html="question.description"></span>
		<span class="stem" v-for="(stem, index) in question.blocks.stems" :key="index">
			<span class="question-info" v-if="!question.description" v-show="index==0">
				<span class="question-number" v-if="questionNr">{{ questionNr }}.</span><a class="refer-info" v-if="refer && !hideRefer" target="__blank" :href="paper">（{{ refer }}）</a>
				<span class="question-score" v-if="showScore" style="color: #999">（{{ question.score }}分）</span>
			</span>
			<span class="stem-body kb_question-content" v-html="stem.stem" v-if="index==0 && !question.description"></span>
			<div class="stem-body kb_question-content" v-html="stem.stem" v-else></div>
			<div class="question-options options-ul" v-if="stem.options">
				<span :class="{option: true,
						'choice-option': true,
						'correct-answer': question.blocks.answers && question.blocks.answers[index].indexOf(opIndex) > -1 && detail
					}" v-for="(option, opIndex) in stem.options" :key="opIndex">
					<span class="option-label kb_question-content">{{opIndex}}</span>.<span class="option-text kb_question-content" v-html="option"></span>
				</span>
			</div>
		</span>
	 	<div style="clear:both"></div>
	</div>
</template>

<script>

	export default {
		props: ['questionNr', 'question', 'hideRefer', 'showScore', 'anchor', 'detail'],
		computed: {
			questionId: function(){
				return 'question_' + this.question.id;
			},
			paper: function(){
				var refs = [];
				if(!this.question.refer_exampapers || this.question.refer_exampapers.length === 0)
					return '';
				var ref = this.question.refer_exampapers[0];
				return '/admin/exampaper/detail/?exampaper='+ref.id;
			},
			refer: function(){
				var refs = [];
				if(!this.question.refer_exampapers || this.question.refer_exampapers.length === 0)
					return '';
				var ref = this.question.refer_exampapers[0];
				if(ref.year)
					refs.push(ref.year);

				if(ref.sch_name)
					refs.push(ref.sch_name);
				else if(ref.province)
					refs.push(ref.province);

				if(ref.category)
					refs.push(ref.category);

				return refs.join('·');
			}
		},
	}
</script>

<style>

	.question {
		padding: 0px;
		position: relative;
	}

	.question-anchor {
		position: absolute;
		top: -50px;
		visibility:hidden;
	}

	.stem-body {
		line-height: 2em;
		word-break: break-all;
	}

	.choice-option {
		display: inline-block;
		margin-bottom: 5px;
		line-height: 1em;
	}

	.ul-1 .choice-option {
		width: 100%;
	}

	.ul-2 .choice-option {
		width: 48%;
	}

	.ul-4 .choice-option {
		width: 24%;
	}

	.refer-info {
		color: #337ab7;
		text-decoration: none;
	}

	.refer-info:hover {
		color: #23527c;
		text-decoration: underline;
	}

	.question-number {
		margin-right: 5px;
	}

	.option-text {
		margin-left: 5px;
	}

	.correct-answer {
		color: #69c170;
	}

	.kb_question-content {
		word-break: break-all;
		line-height: 24px;
	}
</style>



// WEBPACK FOOTER //
// TikuQuestion.vue?e55c0178