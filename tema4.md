# Tema4

## Değişkenler
```css
body {
    --font1: 'Philosopher', sans-serif;
    --font2: 'Antonio', sans-serif;
    
     --radius:0;
    --fancybox-accent-color:var(--main)!important;
    --shadow:3px 3px 20px 0 rgb(40 40 40 / 8%);
    
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


# Belli bir sayfada ara alandaki resmi değiştirme
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


