<template>
    <div>
        <canvas id="canvas" width="512" height="512"></canvas>
    </div>
</template>

<script>
    import {Stage,Shape,Text} from '@createjs/easeljs';
    const WebFont = require('webfontloader');

    const fonts = [
        {
            families: 'M PLUS 1p',
            urls: 'https://fonts.googleapis.com/css?family=M+PLUS+1p'

        },
        {
            families: 'Nico Moji',
            urls: 'https://fonts.googleapis.com/earlyaccess/nicomoji.css'
        },
        {
            families: 'M PLUS Rounded 1c',
            urls: 'https://fonts.googleapis.com/css?family=M+PLUS+Rounded+1c'
        },
        {
            families: 'Hannari',
            urls: 'https://fonts.googleapis.com/earlyaccess/hannari.css'
        },
        {
            families: 'Kokoro',
            urls: 'https://fonts.googleapis.com/earlyaccess/kokoro.css'
        },
        {
            families: 'Sawarabi Mincho',
            urls: 'https://fonts.googleapis.com/css?family=Sawarabi+Mincho'
        },
        {
            families: 'Sawarabi Gothic',
            urls: 'https://fonts.googleapis.com/css?family=Sawarabi+Gothic'
        },
        {
            families: 'Nikukyu',
            urls: 'https://fonts.googleapis.com/earlyaccess/nikukyu.css'
        },
        {
            families: 'Nico Moji',
            urls: 'https://fonts.googleapis.com/earlyaccess/nicomoji.css'
        },
        {
            families: 'Noto Sans JP',
            urls: 'https://fonts.googleapis.com/css?family=Noto+Sans+JP'
        }
    ]

    export default {
        props:['font','fontSize','drawText','backColor','foregroundColor'],
        watch:{
            font(){
                this.draw(this.font,this.fontSize,this.drawText,this.backColor,this.foregroundColor)
            },
            fontSize(){
                this.draw(this.font,this.fontSize,this.drawText,this.backColor,this.foregroundColor)
            },
            drawText(){
                this.draw(this.font,this.fontSize,this.drawText,this.backColor,this.foregroundColor)
            },
            backColor(){
                this.draw(this.font,this.fontSize,this.drawText,this.backColor,this.foregroundColor)
            },
            foregroundColor(){
                this.draw(this.font,this.fontSize,this.drawText,this.backColor,this.foregroundColor)
            }
        },
        mounted() {
            this.draw(this.font,this.fontSize,this.drawText,this.backColor,this.foregroundColor)
        },
        methods:{
            draw:function (font,fontSize,drawText,backColor,foreColor) {
                let fontFamily = fonts.find((obj =>{return obj.families === font}));
                WebFont.load({
                    custom:{
                        families:[fontFamily.families],
                        urls:[fontFamily.urls]
                    },
                    active:function () {
                        let stage = new Stage('canvas');
                        let width = stage.canvas.width;
                        let height = stage.canvas.height;

                        stage.removeAllChildren();
                        let text = new Text(drawText,`${fontSize}px ${font}`,foreColor);
                        text.textAlign = 'center';
                        text.textBaseline = 'middle';
                        text.x = width/2;
                        text.y = height/2;
                        let bounds = text.getBounds();
                        let textWidth = bounds.width;
                        let textHeight = bounds.height;

                        let circle = new Shape();
                        let radius = Math.sqrt((textWidth/2)**2+(textHeight/2)**2);
                        circle.graphics.beginFill(backColor).drawCircle(width/2,height/2,radius);

                        stage.addChild(circle);
                        stage.addChild(text);

                        stage.update();
                    }
                })
            }
        }
    }
</script>

<style scoped>
    canvas{
        border: 3px black solid;
    }
</style>