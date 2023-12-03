## JevilAds.loadAds

전면 광고를 미리 로드한다
- JevilAds.loadAds(param, callback)

#### parameter

- param `json` `require` 
  - adUnitId : `string` `require` 광고 Unit ID
  - type : `string` `require` 광고 종류
    
- callback `function` `require` 
  - r : `boolean` 성공 여부

#### Example code
```javascript
let adUnitId = Jevil.get('OS') =='Android' ? 'ca-app-pub-5134106554966339/2997583641' : 'ca-app-pub-5134106554966339/3446237835'
  JevilAds.loadAds({adUnitId:adUnitId, type:'interstitial'}, function(res){
    if(res.r) {
      
    }
})
```

## JevilAds.showAds

미리 로드해놓은 전면 광고를 보여준다
- Jevil.showAds(param, callback)

#### parameter

- param `json` `require`
  - type : `string` `require` 광고 종류
    
- callback `function` `require` 
  - r : `boolean` 성공 여부

#### Example code
```javascript
JevilAds.showAds({type:'interstitial'}, function(res){
  
})

```