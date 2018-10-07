# dnt-helper
Respect user choice and honor DNT, wrap all the things

## Basic Usage with Google Tag Manager

First ensure that `window.dataLayer` is defined to avoid script errors:

``` javascript
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
//core dataLayer object goes here
});
```

Now wrap the analytics include in the `_dntEnabled` conditional:

``` javascript
if (!_dntEnabled()) {
  (function(w,d,s,l,i,j,f,dl,k,q){
    w[l]=w[l]||[];w[l].push({'gtm.start': new Date().getTime(),event:'gtm.js'});f=d.getElementsByTagName(s)[0];
    k=i.length;q='//www.googletagmanager.com/gtm.js?id=@&l='+(l||'dataLayer');
    while(k--){j=d.createElement(s);j.async=!0;j.src=q.replace('@',i[k]);f.parentNode.insertBefore(j,f);}
  }(window,document,'script','dataLayer',['{{settings.GTM_CONTAINER_ID}}']));
}
```

[Read the blog post](https://medium.com/@schalkneethling/respect-user-choice-do-not-track-6c13b805b256)
