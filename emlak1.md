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

