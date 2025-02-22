# Tema4

## Değişkenler
```css
body {
    --font1: 'Philosopher', sans-serif;
    --font2: 'Antonio', sans-serif;
    
     --radius:0;
    --fancybox-accent-color:var(--main)!important;
    --shadow:3px 3px 20px 0 rgb(40 40 40 / 8%);
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


## Belli bir sayfada ara alandaki resmi değiştirme
```css
#araalan[data-baslik="Paket Servis"]{
    background-image:url("https://img.kod8.in/641/kod829845.jpg")!important;
}


/*Kurumsal haber listeleme ve detay sayfalarında değiştirir*/
  #araalan[data-baslik="Kurumsal"],#araalan[data-kategori="Kurumsal"]{
    background-image:url("https://img.kod8.in/889/-30112022-182228.jpg")!important;
}
```

## Birincil ve ikincil fontları değiştirme
```css
@import url('https://fonts.googleapis.com/css2?family=Philosopher:ital,wght@0,400;0,700;1,400;1,700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Antonio:wght@200;400;600;700&display=swap');

body{
    --font1:'Philosopher', sans-serif;
    --font2:'Antonio', sans-serif;
}
```


## Dekoratif ikonu değiştirme
```css
.decorative-icon:before {
    content: "";
    background: url("https://img.kod8.in/889/9556-1122022-134932.png");
    width: 36px;
    height: 36px;
    display: block;
    background-size: contain;
    background-repeat: no-repeat;
}
```

## İçeriğe Video ekleme
```html
 <video preload="none" loading="lazy" width="100%" height="auto" controls poster="https://cdn.kod8.in/POSTERURL">
  <source src="https://cdn.kod8.in/VIDEOURL" type="video/mp4">
Your browser does not support the video tag.
</video>
```

## Instagram bölümü ekleme
```html
	<script src="https://cdn.jsdelivr.net/gh/stevenschobert/instafeed.js@2.0.0rc1/src/instafeed.min.js"></script>

<script>
AddOnLoadEvent(function(){
    if(document.querySelector(".bizdenhaberler")){
        createInstagramFeedElement();
        renderInstagramFeed();
    }
})


function createInstagramFeedElement(){
    var instaFeedContainer=document.createElement("div")
    instaFeedContainer.innerHTML=`
     <div class="container">
    <div class="row">
          <div class="col-sm-12 col-md-12 col-lg-6 offset-lg-3">
             <div class="heading text-center mb-50">
              <i class="fa fa-star decorative-icon" aria-hidden="true"></i>
              <a href="https://www.instagram.com/humhumbees/" title="İnstagram Adresimiz" target="_blank" rel="nofollow"><h2 class="heading__title">Instagram'da Takip Et</h2>
<a href="https://www.instagram.com/humhumbees/" class="navbar__action-btn navbar__action-btn-reserve btn btn__primary" target="_blank" rel="nofollow"><i class="fa fa-instagram"></i>humhumbees
</a></a>
            
            </div>
            
            </div>
          </div>
        </div>
        </div>
    <div class="col-12 mb-5" id="instafeed">
    
    </div>
    `

    document.querySelector(".bizdenhaberler").insertAdjacentElement('afterend', instaFeedContainer)
}

function renderInstagramFeed(){
var igToken = "IGTOKEN"
	if(document.querySelector("#instafeed")){
		var feed = new Instafeed({
			accessToken: igToken,
			limit:6,
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

## Footer Üzerine Bant (Sponsorluk bandı)
```html
<a href="https://kod8.net" title="Kod8 ve Serbay Sponsorluğunda" target="_blank" class="sponsorluk">  
  Web sitemiz 
  <img class=" lazy" src="https://static.kod8.net/img/ph.png" data-src="https://static.kod8.net/img/tayyarelimani/sirketlogolari/kod8/kod8.png" alt="Serbay ve kod8 Sponsorluğunda" />
sponsorluğunda hazırlanmıştır.
</a>

<style>
  .sponsorluk{
    order:2;
    color: gray;
    font-size: 2em;
    font-weight: 100;
    background: rgb(245,245,245);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1em 0;
}
.sponsorluk img{width:150px;}
@media only screen and (max-width: 600px) {
    .sponsorluk{font-size: 1em;padding: 2em 0;font-weight: 400;}
    .sponsorluk img{width:75px;}
}
  .footer {margin-top: 0!important;order: 2;}
</style>
```
## Footer Üzerine İletişim için bant
```html
<!--Call banner-->

<div class="callBanner" title="İletişime Geç">
  <div class="left">
    <div class="title">İletişime <span>Geç</span></div>
        <div class="subtitle">Daha detaylı bilgi ve teklif almak için bizimle her an iletişime geçebilirsiniz.</div>

    <span class="phone" title="İletişime Geç"></span>
    <a href="https://www.tabeladostu.com/iletisim" title="İletişim" class="navbar__action-btn navbar__action-btn-reserve btn btn__primary m-0">İletişim Formu</a>
  </div>
  <img src="https://cdn.kod8.in/1135/9817-7112023-165159.jpg" alt="İletişime Geç">
</div>

<script>
AddOnLoadEvent(function(){
  var callBanner=document.querySelector(".callBanner");
var targetLinks=callBanner.querySelectorAll(".callBanner .phone");
var phoneNumber=document.querySelector(`footer .contact-box a[href^="tel"]`).innerText;
var phoneNumberLink=document.querySelector(`footer .contact-box a[href^="tel"]`).href;
  callBanner.href=phoneNumberLink;
  
  targetLinks.forEach(function(link){
    link.innerText=phoneNumber
    link.href=phoneNumberLink;
  })
})  
</script>

<style>
  .footer{order:2}
  .anasayfa {
    display: flex;
    flex-direction: column;
}
  .callBanner{
    order:2;
    --height:400px;
    height: var(--height);
    display: flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom: -45px;
    overflow: hidden;
    position: relative;
}

.callBanner .left{
    padding-left: 2em;
    font-size: 2em;
    text-align: left
}

.callBanner .title{
    font-size: 1.5em;
    font-weight: 700;
    text-transform: uppercase;
    color:var(--main)
}

.callBanner .title span{color:var(--dark)}

.callBanner .phone{
    color:var(--dark);
    font-size: 1.7em;
    font-weight: 800;
  display:block;
}

.callBanner > img{
    z-index: -1;
    position: absolute;
    right: 0;
    height: 100%;
}

@media only screen and (max-width: 640px){
    .callBanner{
        font-size: .65em;
    --height: 200px;
    }
  
   .callBanner img{
      width: 100%;
    object-fit: cover;
    opacity: .2;
    }

}

</style>
<!--Call banner-->
```

## Stillendirilmiş Blok Örnekleri
### Anavitrin yapılan sayfanın alt sayfaları için kart stili 1

```css
.anaVitrinler .anaVitrinItem .altSayfalar {
    align-items:unset;
    margin-top: 3em;
    --shadow:none;

}

.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {
    padding-right: 0;
    border-radius: var(--radius);
    margin-bottom:3em;
    border: 1px solid var(--main);

}
    
.anaVitrinler .anaVitrinItem .altSayfalar a {
    flex-direction: column;
} 


.anaVitrinler .anaVitrinItem .altSayfalar a img {
    width: 90%;
    height: auto;
    border-radius: var(--radius);
    margin: -2em 1em 0 5%;
    transition:all 300ms ease;
}

.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa:hover img {
    margin: -2em 1em 1.25em 10%;
    width: 80%;
}

.anaVitrinler .anaVitrinItem .altSayfalar a div .baslik {
    font-size: 1.5em;
    font-weight: 400;
    text-transform: uppercase;
    color: var(--dark);
}

    .anaVitrinler .anaVitrinItem .altSayfalar a .spot {
    display: block;
    width: 100%;
    margin: 0;
    text-align: center;
    color: var(--light);
    font-size: 1em;
    font-style: italic;
}
```

### Ana vitrin alt sayfalar stili (Resimsiz/neden biz vs )
```css
/*Resimsiz Anasayfa Anavitrin*/
@media (min-width:1024px){

.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]:before,
.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]:after  {
  background: var(--darker);
    content: "";
    width:calc(49.5vw - 50%);
    height: 100%;
    z-index: -1;
    position: absolute;
    top: 0;
}

.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]:before  {left: 100%;}
.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]:after  {right: 100%;}
    .anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]  .altSayfalar .altSayfa  .spot{
    display: block;
    color: white;
    opacity: .5
}
    
}

.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]  {background: var(--darker);padding: 1em;}
.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"] > .resim  {display: none;}
.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"] > .detay  {flex: 1 1 100%;margin: 0;}

.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]  .altSayfalar {
    margin: 0!important;
    gap: 1em;
    padding: 0;
    padding-top: 1em;
    align-items: stretch;
}

.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]  .altSayfalar .altSayfa  {
    flex: 0 1 calc(50% - .5em);
    background: var(--darker);
    padding: 1em;
    margin: 0;
    border: 1px solid var(--dark);
}

.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]  .altSayfalar .altSayfa  .image{display: none;}
.anaVitrinler .anaVitrinItem[data-vitrin-sayfa-baslik="Sayfa Başlığı"]  .altSayfalar .altSayfa  .baslik{color: white;font-size: 1.2em;font-family: var(--font2);}
/*/Resimsiz Anasayfa Anavitrin*/

```

### Slider detay yazısı stili
```css

/*Slider*/
.k8Slider .sliderDetay {background: var(--dark)!important;padding: 50px;line-height: 1.2;opacity: 0;top: 33%;}
.k8Slider .imagewithCaption .resim:before {content: unset;}
.k8Slider .sliderDetay .baslik {display: flex;flex-direction: column;text-transform: uppercase;font-weight: 200;}
.k8Slider .sliderDetay .baslik b {font-weight: 800;}
.k8Slider .sliderDetay .aciklama {font-size: 1.75em;line-height: 1.5;font-weight: 400;opacity: .75;border-top: 1px solid var(--light);padding-top:.5em;}

.k8Slider .sliderDetay:before {
    content: "";
    position: absolute;
    inset: -1em;
    z-index: -1;
    background: var(--light);
    clip-path: polygon(0 60.00px,60.00px 0,100% 0,100% 100%,0 100%,0 60.00px,2px  calc(60.00px + 2px),2px calc(100% - 2px),calc(100% - 2px) calc(100% - 2px),calc(100% - 2px) 2px,calc(60.00px + 2px) 2px,2px calc(60.00px + 2px));
}


.k8Slider .is-visible .sliderDetay {-webkit-animation:slide-in-right .5s cubic-bezier(.25,.46,.45,.94) both;animation:slide-in-right .5s cubic-bezier(.25,.46,.45,.94) both}

.k8Slider .is-visible .baslik {-webkit-animation:slide-in-bottom .5s cubic-bezier(.25,.46,.45,.94) both;animation:slide-in-bottom .5s cubic-bezier(.25,.46,.45,.94) both}
.k8Slider .is-visible .aciklama {-webkit-animation:slide-in-bottom .5s cubic-bezier(.25,.46,.45,.94) 1s both;animation:slide-in-bottom .5s cubic-bezier(.25,.46,.45,.94) .25s both}
@-webkit-keyframes slide-in-right{0%{-webkit-transform:translateX(1000px);transform:translateX(1000px);opacity:0}100%{-webkit-transform:translateX(0);transform:translateX(0);opacity:1}}@keyframes slide-in-right{0%{-webkit-transform:translateX(1000px);transform:translateX(1000px);opacity:0}100%{-webkit-transform:translateX(0);transform:translateX(0);opacity:1}}
@-webkit-keyframes slide-in-bottom{0%{-webkit-transform:translateY(1000px);transform:translateY(1000px);opacity:0}100%{-webkit-transform:translateY(0);transform:translateY(0);opacity:1}}@keyframes slide-in-bottom{0%{-webkit-transform:translateY(1000px);transform:translateY(1000px);opacity:0}100%{-webkit-transform:translateY(0);transform:translateY(0);opacity:1}}

```
## Script ve Diğer Düzenlemeler
### Ürün Galeriside Slider En Boy Oranını Değiştirme
```js
AddOnLoadEvent(function(){
	mainProductSlider.options.heightRatio="1"
	mainProductSlider.refresh()
})
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
 .cozumortaklari .carousel{display: grid;grid-template-columns: repeat(auto-fill,minmax(170px,1fr));margin-top: 1em;}
.cozumortaklari .carousel > .client{border: 1px solid #eeeeee;padding: 1em;}
</style>
```


## Rakamları animasyonlu saydırma
```js
 // Sayıların başlangıç ve bitiş değerlerini tanımlayın
const numbers = [...document.querySelectorAll('.rakam')].map(function(rakam){return { element: rakam, start: 0, duration: 4000 }})

// Sayıların bitiş değerlerini metinden dinamik olarak al
function extractNumberFromText(element) {
  const textContent = element.textContent; 
  const numberMatch = textContent.match(/\d+/); // Sayıyı metinden çıkart
  return numberMatch ? parseInt(numberMatch[0], 10) : 0; // Sayıyı döndür
}

// Sayıları artırma fonksiyonu
function animateNumber(element, start, end, duration) {
  let startTime = null;

  function incrementNumber(timestamp) {
    if (!startTime) startTime = timestamp;
    let progress = timestamp - startTime;
    let current = Math.min(start + (progress / duration) * (end - start), end);
    element.innerText = Math.floor(current);

    if (current < end) {
      requestAnimationFrame(incrementNumber);
    }
  }

  requestAnimationFrame(incrementNumber);
}

// Intersection Observer ile animasyon başlatma
const observerOptions = {
  root: null, // Varsayılan olarak viewport
  threshold: 0.1, // %10'u görünür olduğunda tetikle
};

const observer = new IntersectionObserver((entries, observer) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const element = entry.target;
      const numberItem = numbers.find(item => item.element === element);
      if (numberItem) {
        const endValue = extractNumberFromText(numberItem.element); // Yazıdan sayıyı çıkar
        animateNumber(numberItem.element, numberItem.start, endValue, numberItem.duration);
        observer.unobserve(numberItem.element); // Bir kere tetiklendikten sonra gözlemlemeyi bırak
      }
    }
  });
}, observerOptions);

// Her sayı elemanını gözlemle
numbers.forEach(item => {
  observer.observe(item.element);
});
  
```



