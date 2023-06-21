# Emlak1

## Değişkenler
```css
body {
    --hue: 6;
    --birincil: #EB220C;
    --ikincil: #171219;
    --beyaz: #FFFFFF;
    --siyah: #171219;
}

```


## Instagram Bloğu ekleme
```html
<script src="https://cdn.jsdelivr.net/gh/stevenschobert/instafeed.js@2.0.0rc1/src/instafeed.min.js"></script>

<script>
AddOnLoadEvent(function(){
    if(document.querySelector(".emlaklar")){
        createInstagramFeedElement();
        renderInstagramFeed();
    }
})


function createInstagramFeedElement(){
    var instaFeedContainer=document.createElement("div")
    instaFeedContainer.innerHTML=`
 
    
    
    <section class="blog-wrap-layout1 bg-accent100 anasayfadainstagram anasayfadafotogaleri mb-5">
		<div class="container">
			<div class="container section-heading heading-dark text-center heading-layout1">
				<a href="https://www.instagram.com/realtyworldduzce/" title="İnstagram Adresimiz"><h2 class="display-4 pb-3">Instagram'da Takip Et</h2></a>
			</div>
			<section id="instafeed">
    </section>
     </div>
      </section>
    `

    document.querySelector(".emlaklar").insertAdjacentElement('afterend', instaFeedContainer)
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
			<img src="{{image}}" alt="Instagram Sayfamız" class="img-fluid">
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
## Ana Vitrin Alt Sayfalar Stili 2 (Dikey Kart)
```css
 /*Anavitrin alt sayfalar stili*/
.anaVitrinler .anaVitrinItem .altSayfalar {
    align-items:unset;
}

.anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {
    padding-right: 0;
    border-radius: 0;
    margin-bottom:2em;
    background: var(--ikincil)
}
    
.anaVitrinler .anaVitrinItem .altSayfalar a {
    flex-direction: column;
} 

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
.anaVitrinler .anaVitrinItem .altSayfalar a .spot {
    display: none;
}
    
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
    .anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {
    overflow: :hidden;
}
  .anaVitrinler .anaVitrinItem .altSayfalar .altSayfa {flex: 0 1 100%;} 
}
  /*/ anavitrin alt sayfalar stili*/

```

## Ana Sayfa Çözüm Ortakları Sliderı bozup Grid Yapma
```html
<!--Çözüm Ortakları Sliderı Grid Yapma -->

<script>
    setTimeout(function(){
      $(".our-clients .owl-carousel").data('owl.carousel').destroy()
  },1000) 
</script>
<style>
 .our-clients .owl-carousel{display: grid;grid-template-columns: repeat(auto-fill,minmax(170px,1fr));margin-top: 1em;}
.our-clients .owl-carousel .item{border: 1px solid #eeeeee;}
</style>
```


