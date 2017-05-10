<template>
    <div id="container"></div>
</template>

<style scoped>
    #container {
        margin: 20px;
        width: 200px;
        height: 100px;
    }
</style>

<script>
    import ProgressBar from 'progressbar.js';

    export default {
        data(){
            return {};

        },
        props: {
            required: false,
            type: {
                type: String,
                default: 'circle'
            },
            width: {
                type: String,
                default: '200px',
            },
            height: {
                type: String,
                default: '200px',
            },
            strokeWidth: {
                type: Number,
                default: 6
            },
            easing: {
                type: String,
                default: 'easeInOut'
            },
            duration: {
                type: Number,
                default: 1500
            },
            color: {
                type: String,
                default: '#FFEA82'
            },
            trailColor: {
                type: String,
                default: "#eee"
            },
            trailWidth: {
                type: Number,
                default: '1'
            },
            to: {
                type: String,
                default: "1.0"
            }
        },
        mounted(){
            const properties = {
                strokeWidth: parseFloat(this.strokeWidth),
                easing: this.easing.trim(),
                duration: parseInt(this.duration),
                color: this.color.trim(),
                trailColor: this.trailColor.trim(),
                trailWidth: parseFloat(this.trailWidth)
            };
            let bar = null;

            if (this.type.toLowerCase() === 'circle') {
                bar = new ProgressBar.Circle('#container', properties);
            }
            else if (this.type.toLowerCase() === 'semi-circle') {
                bar = new ProgressBar.SemiCircle('#container', properties);
            }
            else if (this.type.toLowerCase() === 'line') {
                bar = new ProgressBar.Line('#container', properties);
            }
            else if (this.type.toLowerCase() === 'svg') {
                bar = new ProgressBar.Line('#container', properties);
            }
            else {
                throw new Error(`ProgressBar Error : Invalid type props (${this.type}) sent. Must be line, circle, semi-circle, svg.`);
            }

            bar.animate(this.to);
        }

    };

</script>