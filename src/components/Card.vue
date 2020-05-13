<template>
    <div class="col-md-6 col-6">
        <div class="cards-item">
            <span class="label-vip"></span>
            <div class="cards-title">
                <h5>{{titulo}}</h5>
            </div>
            <p>
                {{info}}
            </p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['titulo', 'info']
}
</script>

<style>
.cards-item {
    background-color: #fff;
    text-align: center;
    padding: 35px;
    -webkit-border-radius: 2px;
    -webkit-background-clip: padding-box;
    -moz-border-radius: 2px;
    -moz-background-clip: padding;
    border-radius: 2px;
    background-clip: padding-box;
    position: relative;
    -webkit-transition: all .3s ease;
    -moz-transition: all .3s ease;
    -o-transition: all .3s ease;
    transition: all .3s ease;
    color: #24232b;
    margin-top: 30px;
}
.label-vip {
    color: #fff;
    display: block;
    width: 90px;
    height: 90px;
    position: absolute;
    right: 0px;
    top: 0;
}
.cards-item .label-vip:before {
    content: "";
    position: absolute;
    z-index: 0;
    width: 0;
    right: 0;
    height: 0;
    border-style: solid;
    border-width: 0 90px 90px 0;
    border-color: transparent #027ABF transparent;
}

.cards-item h5 {
    text-align: center;
    margin-top: 0;
    font-weight: 800;
    font-size: 21px;
    line-height: 1.6em;
    color: #000;
}

.cards-item p{
    font-size: 40px;
}

@media(max-width: 768px){
    .cards-item h5 { 
        font-size: 14px;
        line-height: 1.2em;
    }
    .cards-item .label-vip::before {
        border-width: 0 60px 60px 0;
    }
    .cards-item p {
        font-size: 19px;
        text-align: center;
    }
}

</style>
