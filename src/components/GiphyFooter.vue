<template>
    <div id="footer">
        <div id="footer-section-1"><img class="hire"
            src="https://media4.giphy.com/media/MbhTDqkrbROYv3izOv/giphy.gif?cid=ecf05e47jvx2akfjoaimoxzjk72is4hnsw2rrbx4yrsul619&rid=giphy.gif&ct=s">
        </div>
        <p id="footer-section-2">Powered by <a class="hire" href="https://vuejs.org/">Vue.js</a><br> Developed by Nic Moorhouse</p>
        <div id="footer-section-3"><img class="hire-2"
                src="https://media2.giphy.com/media/eiMn6aBwpkSCffKOG0/giphy.gif?cid=ecf05e47zhha2i8sz0q7arbrwis2yfrmz4o1kxof5ui9fh7w&rid=giphy.gif&ct=g">
        </div>
    </div>
</template>

<script>
export default {
    name: 'GiphyFooter', //import to vue
    props: {
        msg: String,
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#footer {
    height: 8em;
    background-color: #d5ffff
}
.text {
    width: 30%
}
/* first image container  */
#footer-section-1 {
    width: 33%;
    float: left;
    padding-top: 1em;
}
/* footer text */
#footer-section-2 {
    width: 33%;
    float: left;
    padding-top: 2em;
    font-size: 18px;
    line-height: 1.4;
    font-weight: bold;
}
/* second image container  */
#footer-section-3 {
    width: 33%;
    float: left;
    padding-top: 2em;
}
.hire-2 {
    width: 18%;
}
.hire {
    width: 25%;
}
</style>