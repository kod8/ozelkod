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
var igToken = "IGQVJYLUZAqXzZAyaEctQzdtcmtxd2h1eXBQMDNkUk9VUFlpRWxPOHBsTS1TUGNPMlMtR0dWQXVvdjZAOZAkRqcFJPUlJfYnJXZAWJTMjFDOTB6SGpSa0wwb3dYSHg5d1lMZAllhVUEzMjIzY01iY2lxa0xxdQZDZD"
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

