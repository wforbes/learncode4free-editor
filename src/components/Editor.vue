<template>
	<v-container>
		<v-row class="">
			<v-col cols="12">
				<span class="text-h2 font-weight-bold">Editor</span>
			</v-col>
			<v-container>
				<v-row justify="center" class="ma-0">
					<v-col cols="9" class="ma-0 pa-0">
						<v-card class="pl-3 pr-3 pt-1 ma-0">
							<v-row>
								<v-col cols="2" class="ma-0">
									<span>Font Size</span>
									<v-select v-model="editorFontSize" :items="editorFontSizeRange" solo class="pa-0 ma-0"></v-select>
								</v-col>
							</v-row>
						</v-card>
					</v-col>
				</v-row>
				<v-row justify="center" class="ma-0">
					<v-col cols="9" class="ma-0 pa-0">
						<editor v-model="content" ref="ace" @init="editorInit" lang="javascript" theme="monokai" width="100%" height="600"></editor>
					</v-col>
				</v-row>
				<v-row>
					<v-col>
						<v-btn @click="runCode">Run</v-btn>
					</v-col>
				</v-row>
				<v-row>
					<v-col>
						<span>{{output}}</span>
					</v-col>
				</v-row>
			</v-container>
		</v-row>
	</v-container>
</template>

<script>
//https://blog.bitsrc.io/build-a-js-interpreter-in-javascript-using-acorn-as-a-parser-5487bb53390c
//https://www.npmjs.com/package/acorn
//https://www.npmjs.com/package/vue2-ace-editor
import editor from 'vue2-ace-editor';
export default {
	name: 'Editor',
	components: {
		editor,
	},
	data(){
		return {
			content: null,
			editorFontSize: 0,
			editorFontSizeRange: [],
			output: ""
		};
	},
	watch: {
		editorFontSize(newVal) {
			this.$refs.ace.editor.setFontSize(newVal);
		}
	},
	created() {
	},
	methods: {
		runCode(){
			let editor = this.$refs.ace.editor;
			console.log(editor);
		},
		editorInit(){
            require('brace/ext/language_tools') //language extension prerequsite...
            require('brace/mode/html')                
            require('brace/mode/javascript')    //language
            require('brace/mode/less')
            require('brace/theme/monokai')
			require('brace/snippets/javascript') //snippet
			const editor = this.$refs.ace.editor
			this.editorFontSize = editor.getFontSize();
			for(let i = 8; i < 30; i++){
				this.editorFontSizeRange.push(i+1);
			}
        }
	}
};
</script>
