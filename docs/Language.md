## 개요 
다국어에 대한 정보를 설정하거나 가져온다.
DAB 콘솔에 입력된 다국어 텍스트와 
설정된 언어코드(Jevil.setLanguage)에 따라 자동으로 각 언어에 맞게 텍스트가 변경된다
예를 들어, '안녕하세요' 와 'Hello'가 이미 DAB콘솔에 입력되어 있다면
key는 '안녕하세요'이고 번역(en)은 Hello이다

## Jevil.getLanguage

현재 언어 설정을 가져온다
각 언어 코드는 ISO_3166-1_alpha-2 의 소문자이다
기존에 설정한 언어가 없으면 현대 휴대폰에 설정된 언어를 가져온다

- Jevil.getLanguage()

#### Example code
```javascript
let lang = Jevil.getLanguage()
if(lang == 'ko')
    ;
```

## Jevil.setLanguage

현재 언어를 설정한다
각언어 코드는 ISO_3166-1_alpha-2 의 소문자이다

- Jevil.setLanguage(lang)

#### parameter

- lang `string` `require` ISO_3166-1_alpha-2 의 소문자

#### Example code
```javascript
Jevil.setLanguage('ko')
```


## Jevil.trans

특정 키에 대한 번역 텍스트를 준다
번역이 없으면 key를 그대로 반환한다 


- Jevil.trans(key)

#### parameter

- key `string` `require` 번역할 텍스트

#### Example code
```javascript
let text = Jevil.trans('안녕하세요')
if(text == 'Hello')
    ;
```
