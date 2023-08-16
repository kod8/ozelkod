# Tema3

## Değişkenler
```css
body {
    
    --fancybox-accent-color:var(--main)!important;
    --aspect-ratio:calc(16 / 9);
    --gallery-aspect-ratio:calc(1);
    
     --hue: 46;
    --white: hsl(0, 0%, 95%);
    --lighter: hsl(0, 50%, 100%);
    --hue: 46;
    --black: hsl(0, 0%, 5%);
    --main: hsl(46deg 95% 54%);
    --dark: #f9c518;
    --darker: #3a3a3a;
    --light: #eee;
}

```
## Koyu Header Stili
```css

/*Koyu Header stili*/
.template-main-menu nav > ul > li > a,.template-main-menu nav > ul > li ul.dropdown-menu-col-1 li a {
    text-transform: uppercase;
    font-weight: 400;
}

header:not(.menu-sticky) .header-menu-layout1 {background: var(--dark);}
header:not(.menu-sticky) .header-top-bar  {background: var(--main);
border-bottom:  1px solid var(--dark);
}

header:not(.menu-sticky) .temp-logo .dark {
display: block!important;
}


header:not(.menu-sticky) .temp-logo .light {
display: none!important;
}
.template-main-menu nav a{font-weight: 800!important}

header:not(.menu-sticky) .template-main-menu nav .dropdown-menu-col-1 li{background: var(--dark);}
header:not(.menu-sticky) .template-main-menu nav .dropdown-menu-col-1 li a:hover{background: var(--main)!important;}
header:not(.menu-sticky) .template-main-menu nav > ul > li a{color: white!important;}
header.menu-sticky .template-main-menu nav > ul > li{border-right: 1px solid var(--light);}
header.menu-sticky .template-main-menu nav > ul > li:first-child{border-left: 1px solid var(--light);}
/*/Koyu Header stili*/
```


## Telefonla ara butonu ekleme(Sol alt sabit ikonlar)

```html

<style>
  
   .fixedButtons [title="Hemen Arayın"]{
    width: 110px!important;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 1em;
}

  .fixedButtons [title="Hemen Arayın"]:after {
    width: 50px;
    line-height: 1;
    content: "Hemen Ara";
    font-size: 12px;
    border-radius: 50px;
    color: #fff;
    font-family: var(--font2);
    font-weight: 800;
}
</style>

<script>
  
AddOnLoadEvent(function(){
var tel=document.querySelector(".footer-contact-info .fas.fa-phone").nextSibling.textContent.replaceAll(" ","");
var telefonButton = document.createElement("a");
telefonButton.title="Hemen Arayın"
telefonButton.href="tel:"+tel;
telefonButton.target="_blank"
telefonButton.style.background="green";

telefonButton.innerHTML=`
<i class="fas fa-phone"></i>
`

document.querySelector(".fixedButtons").appendChild(telefonButton)

})
</script>
```

## Açılır Mesaj Yazılabilir Whatsapp Butonu
```html
<!-- Floating Whatsapp Button -->
<div id="WAButton"></div>

<link rel="stylesheet" href="https://rawcdn.githack.com/rafaelbotazini/floating-whatsapp/3d18b26d5c7d430a1ab0b664f8ca6b69014aed68/floating-wpp.min.css">
<script type="text/javascript" src="https://rawcdn.githack.com/rafaelbotazini/floating-whatsapp/3d18b26d5c7d430a1ab0b664f8ca6b69014aed68/floating-wpp.min.js"></script>
<script type="text/javascript">
  $(function() {
    $('#WAButton').floatingWhatsApp({
        phone: '+'+document.querySelector(".whatsappButton").href.split("phone=")[1].split("&")[0], 
        headerTitle: 'Bize WhatsApptan Yazın!',
        popupMessage: 'Merhaba, size nasıl yardımcı olabilirim?', 
        showPopup: true,
        buttonImage: '<img src="https://rawcdn.githack.com/rafaelbotazini/floating-whatsapp/3d18b26d5c7d430a1ab0b664f8ca6b69014aed68/whatsapp.svg" />',
        position: "right",
        zIndex: 99,
        autoOpenTimeout:3000
    });
});
</script>
```


## Instagram bloğu ekleme
```html
<script src="https://cdn.jsdelivr.net/gh/stevenschobert/instafeed.js@2.0.0rc1/src/instafeed.min.js"></script>
<script>
AddOnLoadEvent(function(){
    if(document.querySelector(".anaVitrinler")){
        createInstagramFeedElement();
        renderInstagramFeed();
    }
})

function createInstagramFeedElement(){
    var instaFeedContainer=document.createElement("div")
    instaFeedContainer.innerHTML=`
    <div class="section-heading text-center text-white heading-light heading-layout1">
		<h2>Sosyal Medyada Biz <i class="fab fa-instagram"></i></h2>
	</div>
        <div class="col-12 mb-5" id="instafeed">
    </div>
    `
    instaFeedContainer.classList.add("w-100")
    instaFeedContainer.classList.add("p-5")
    instaFeedContainer.classList.add("my-3")
    instaFeedContainer.classList.add("container-fluid")
    instaFeedContainer.style.background="var(--dark)"
    document.querySelector(".anaVitrinler").insertAdjacentElement('afterend', instaFeedContainer)
}

function renderInstagramFeed(){
var igToken = "IGTOKEN"
	if(document.querySelector("#instafeed")){
		var feed = new Instafeed({
			accessToken: igToken,
			limit:12,
			transform: function(item) {
				var d = new Date(item.timestamp);
				item.date = d.toLocaleString('default', { day:"numeric", month: 'long', year:"numeric" });
				item.caption=item.caption ?    item.caption.substring(0,100)+"..." : ""
				return item;
			},
			"template":`
<div class="instaImageItem">
<a href="{{link}}" title="Instagram Sayfamız" target="_blank" rel="nofollow" class="aspect-box d-block" >
			<img src="{{image}}" alt="Instagram Sayfamız">
			<span class="btn">Görüntüle</span>
</a>
</div>
`
});
feed.run();
}
}


</script>
<style>
  #instafeed{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1em;
}

.instaImageItem {
    position: relative;
    --aspect-ratio: 1;
}

.instaImageItem a span{
    display: flex;
    position: absolute;
    top: 0;
    left: 0;
    width:100%;
    height: 100%;
    background: var(--main);
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1em;
    font-weight: 100;
    letter-spacing: 2px;
    text-transform: uppercase;
    opacity: 0;
    backdrop-filter: contrast(0);
    -webkit-backdrop-filter: contrast(0);
    transition: all .5s ease;
}

.instaImageItem:hover a span{
        letter-spacing: 4px;
        opacity: .5;
}

@media (max-width: 767px){
    #instafeed{
        grid-template-columns: 1fr 1fr;
    }
}
</style>
```

## Anavitrin alt sayfaları kart stili (dikey)
```css
/*Anavitrin alt sayfalar stili*/
.anaVitrinler .anaVitrinItem .altSayfalar {align-items:unset;}
.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {
    padding-right: 0;
    border-radius: 0;
    margin-bottom:2em;
    background: var(--darker)
}
    
.anaVitrinler .anaVitrinItem .altSayfalar a {flex-direction: column;} 
.anaVitrinler .anaVitrinItem .altSayfalar a:hover{color:white;}
.anaVitrinler .anaVitrinItem .altSayfalar i {
    flex-grow:2; 
    order: 1;
    transform: rotate(90deg);
    line-height: 0;
    background: white;
    padding: 10px;
    border-radius: 50%;
    width:2em;
    height: 2em;
    display:flex;
    align-items:center;
    justify-content:center;
    margin-bottom:1em;
    margin-top: -1em
}

.anaVitrinler .anaVitrinItem .altSayfalar a img {
    width: 90%;
    height: auto;
    border-radius: 0;
    margin: -2em 1em 2em 5%;
    transition:all 300ms ease;
}

.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa:hover img {
    margin: -2em 1em 3em 10%;
    width: 80%;
}

.anaVitrinler .anaVitrinItem .altSayfalar a div .baslik {
    font-size: 1.25em;
    font-weight: 800;
    text-align: center;
    display: block;
}

  .anaVitrinler .anaVitrinItem .altSayfalar a .spot {
    display: block;
    width: 100%;
    font-size: 1em;
    margin: 0;
    text-align: center;
    color: white;
    font-weight: 200;
}

@media only screen and (max-width: 600px) {
.anaVitrinler .anaVitrinItem .altSayfalar a .spot {display: none;}
.anaVitrinler .anaVitrinItem .altSayfalar a img {
    width: 100%;
    border-radius: 0;
    margin: 0;
}

.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa:hover img {
    margin: 0;
    width: 100%;
}
  .anaVitrinler .anaVitrinItem .altSayfalar i {
    margin-left: 0;
    margin-top: .5em;
}
.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {overflow: :hidden;}
  .anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {flex: 0 1 100%;} 
}
/*/ anavitrin alt sayfalar stili*/
```

## Ana Sayfa Çözüm Ortakları Sliderı bozup Grid Yapma
```html
<!--Çözüm Ortakları Sliderı Grid Yapma -->
<script>
    setTimeout(function(){
      
     $('.cozumortaklari .owl-carousel').trigger('destroy.owl.carousel').removeClass('owl-carousel owl-loaded');
  },1000) 
  </script>
<style>
 .cozumortaklari .owl-stage-outer{display: grid;grid-template-columns: repeat(auto-fill,minmax(170px,1fr));margin-top: 1em;}
.cozumortaklari .owl-stage-outer > div{border: 1px solid #eeeeee;padding: 1em;}
</style>
```


## Kartlardaki gradyanı kaldırma
```css

/*Kartlardaki gradyanı kaldır*/
.departments-box-layout5{height: calc(100% - 1em);}

.departments-box-layout5 .item-img{
   display: flex;
    flex-direction: column;
    background:var(--dark);
    height: 100%;
}


.departments-box-layout5 .item-img img{border-radius: 0;height: auto;object-fit: contain}
.departments-box-layout5 .item-img:before{content: unset;}


.departments-box-layout5 .item-img .item-content {
    position: initial;
    width: 100%;
    padding: 1em 2em;
    background: var(--dark);
}

.departments-box-layout5 .item-img .item-content .item-btn {
   visibility: visible;
    opacity: 1;
    border-radius: 0;
}

.departments-box-layout5:hover  {
    transform:perspective(1200px) scale(1) rotateY(0deg) rotateX(5deg) translate3d(0,0, -50px);
    box-shadow: unset;
}

.departments-box-layout5:hover .item-content {transform:unset;}

.departments-box-layout5 .item-img .item-content p {
    opacity: .8;
    visibility: visible;
}
/*/Kartlardaki gradyanı kaldır*/
```





