
## JevilWebRtc.start

이미 kinesis 채널이 생성된 상태에서 호출된다
새로운 화면으로 서로 1:1 화상채팅을 하게된다
새로운 화면은 DAB가 제공하는 화면으로서 커스터마이징은 할 수 없다

- Jevil.start(param, callback)

#### parameter

- param `json` `require` WebView 노드 명
    - arn : `string` `require` 
    AWS Kinesis channel에 대한 arn
    - region : `string` `require` 
    AWS Kinesis Region
    - accessKeyId : `string` `require` 
    AWS accessKeyId 이며, kinesis 관련된 권한만 할당하길 권장한다(클라이언트에 노출되므로)
    - secretAccessKey : `string` `require` 
    AWS secret Access Key 이며, kinesis 관련된 권한만 할당하길 권장한다(클라이언트에 노출되므로)
    - channelInfo : `json` `require` 
    AWS Kinesis 채널에 관련된 정보로서 다음과 같다
    channelInfo Example 참조
    - isMaster : `string` `require`
    마스터 여부
    - isAudioSent : `string` `require` 
    오디오 송출여부
    - isVideoSent : `double` `require`
    비디오 송출여부
    - clientId : `string` `optional` 
    web rtc에 접속할 clinetId이며, null일경우 랜덤하게 결정된다
    
- callback `function` `require` 
    - event `string` `require`  이벤트 종류
    - data `json` `require`  이벤트의 상세 정보
    
#### channelInfo Example
```javascript
let channelInfo = {
  "ResourceEndpointList": [
    {
      "Protocol": "HTTPS",
      "ResourceEndpoint": "https://r-424ef825.kinesisvideo.ap-northeast-2.amazonaws.com"
    },
    {
      "Protocol": "WSS",
      "ResourceEndpoint": "wss://v-05a6c86a.kinesisvideo.ap-northeast-2.amazonaws.com"
    }
  ],
  "IceServerList": [
    {
      "Uris": [
        "turn:15-165-75-23.t-cf94f1b5.kinesisvideo.ap-northeast-2.amazonaws.com:443?transport=udp",
        "turns:15-165-75-23.t-cf94f1b5.kinesisvideo.ap-northeast-2.amazonaws.com:443?transport=udp",
        "turns:15-165-75-23.t-cf94f1b5.kinesisvideo.ap-northeast-2.amazonaws.com:443?transport=tcp"
      ],
      "Username": "1694181504:djE6YXJuOmF3czpraW5lc2lzdmlkZW86YXAtbm9ydGhlYXN0LTI6MjMxMzMwNDIxMTc5OmNoYW5uZWwvdGVzdDEvMTY5Mjg0MzQ4NDM5NA==",
      "Password": "hV3xUF0vaArlpzPjWmcz6SZtyfMUSZqklSyo2vmKewQ=",
      "Ttl": 300
    },
    {
      "Uris": [
        "turn:54-180-126-69.t-cf94f1b5.kinesisvideo.ap-northeast-2.amazonaws.com:443?transport=udp",
        "turns:54-180-126-69.t-cf94f1b5.kinesisvideo.ap-northeast-2.amazonaws.com:443?transport=udp",
        "turns:54-180-126-69.t-cf94f1b5.kinesisvideo.ap-northeast-2.amazonaws.com:443?transport=tcp"
      ],
      "Username": "1694181504:djE6YXJuOmF3czpraW5lc2lzdmlkZW86YXAtbm9ydGhlYXN0LTI6MjMxMzMwNDIxMTc5OmNoYW5uZWwvdGVzdDEvMTY5Mjg0MzQ4NDM5NA==",
      "Password": "SOU5dcIUgHJAqVcrMSyrrpaLCO8nMELOECLDtrg014A=",
      "Ttl": 300
    }
  ],
  "endpointsByProtocol": {
    "HTTPS": "https://r-424ef825.kinesisvideo.ap-northeast-2.amazonaws.com",
    "WSS": "wss://v-05a6c86a.kinesisvideo.ap-northeast-2.amazonaws.com"
  }
}
```

#### Example code
```javascript
function start_viewer_video() {
  Jevil.startLoading()
  Jevil.getThen('https://api.mondayless.co.kr/api/webrtc/live/test/get/viewer', function(res) {
    Jevil.stopLoading()  
    if(res) {
      res.channelName = 'test1'
      
      //optional
      res.isMaster = false
      res.isAudioSent = true
      res.isVideoSent = true
      res.isFront = true
      
      Jevil.log('param', res)
      JevilWebRtc.start(res, function(event, res) {
    
      })  
    }
  })
}
```

특정 뷰를 web rtc 뷰로 만드는 법은 blockRule WebRtc 참조