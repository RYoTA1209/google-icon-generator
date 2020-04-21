<template>
    <div class="uk-container uk-container-small">
        <h1 class="uk-heading-line uk-text-center"><span>Google Icon Generator</span></h1>

        <form class="uk-form-horizontal">

            <div class="uk-margin">
                <label for="drawText" class="uk-form-label">テキスト</label>
                <div class="uk-form-controls">
                    <input type="text" name="draw-text" id="drawText" class="uk-input" v-model="drawText"><br>
                </div>
            </div>


            <div class="uk-margin">
                <label for="font-select" class="uk-form-label">フォント</label>
                <div class="uk-form-controls">
                    <select name="font" id="font-select" class="uk-select" v-model="font">
                        <option value="Hannari">はんなり明朝</option>
                        <option value="Kokoro">こころ明朝</option>
                        <option value="Sawarabi Mincho">さわらび明朝</option>
                        <option value="Sawarabi Gothic">さわらびゴシック</option>
                        <option value="Nikukyu">ニクキュウ</option>
                        <option value="Nico Moji">ニコモジ</option>
                        <option value="Noto Sans JP">Noto Sans JP</option>
                    </select>
                </div>
            </div>


            <div class="uk-margin">
                <label for="font-size" class="uk-form-label">フォントサイズ</label>
                <div class="uk-form-controls">
                    <input type="range" name="font-size" id="font-size" class="uk-range" value="36" min="1" max="120" v-model="fontSize">
                </div>
            </div>


            <div class="uk-margin">
                <label for="" class="uk-form-label">背景色</label><br>
                <Swatches v-model="backColor" inline></Swatches>
            </div>


            <div class="uk-margin">
                <label for="" class="uk-form-label">文字色</label><br>
                <Swatches v-model="foreColor" inline></Swatches>
            </div>

        </form>


        <draw v-bind:font="font" v-bind:font-size="fontSize" v-bind:drawText="drawText" v-bind:back-color="backColor" v-bind:foreground-color="foreColor" class="uk-flex uk-flex-center"/>
    </div>
</template>

<script>
    import Draw from './Draw';
    import Swatches from 'vue-swatches';

    import 'vue-swatches/dist/vue-swatches.css';

    import UIkit from 'uikit';
    import 'uikit/dist/css/uikit.css';
    import 'uikit/dist/css/uikit.min.css'

    export default {
        data(){
            return {
                font: 'Hannari',
                fontSize: 32,
                drawText: '',
                backColor: '#000000',
                foreColor: '#FFFFFF'
            }
        },
        components:{Draw,Swatches,UIkit},
    }
</script>

<style scoped>

</style>