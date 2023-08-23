# What is block?

Block은 특정 Sketch Node를 Android Natvie 뷰로 만들기 위한 설정이다. 다음 화면과 같이 sketch의 특정 Node를 Block을 지정하면 다음과 같이 화면이 웹상에 보이며, 다양한 Block Rule을 설정할 수 있다

![Alt text](block-screen.png)

그리고 다음과 같은 Block Rule을 통해 클릭했을때, 동적 이미지, 동적 텍스트, 리스트 등으로 앱을 다이나믹하게 구현 할 수 있다

# data 참조
모든 block룰은 Screen의 data라는 변수를 기본적으로 참조한다

```javascript
data.my_name = 'Mondayless'
```
위와 같은 코드가 Screen에 있고 블럭룰중 하나인 Text Mappging에 특정 노드에 my_name을 걸어두면 
앱 화면의 그 텍스트가 'Mondayless'가 된다



# Block If Condition 

# Block Rule

## Sketch Root

Sketch의 특정 노드를 블록으로 등록한다
모든 Block은 이 단계를 먼저 해야한다

![Alt text](block_sketch_root.png)

![Alt text](block_node_select.png)

## Input Mapping

특정 Text 노드를 Input으로 만든다. 

- Target Node `string` `require` Input으로 만들 스캐치 노드 
- Dat Key `string` `require` data에 저장될 키
- Password `boolean` `optional` 인풋이 Password가 된다
- Action Button Type of KeyPad `optional` 앱에 뜨는 키패드의 Action 버튼의 형태를 지정한다
- Complete Click Action `script` `optional` 
앱에 뜨는 키패드의 Action 버튼을 눌렀을 때 발동된다
예를들어 Jevil 함수를 호출할수 있다.
    - 현재는 1줄로만 입력 가능하며 Jevil.script('myfunction()') 형태로만 호출가능 하다

- Input Type `optional` 키패드의 모양과 입력 가능한 형태를 지정한다
    - TEXT `default` 기본적인 한줄입력 text 이다
    - MULTILINE 여러줄을 입력할 수 있다
    - NUMBER 전화번호와 같이 숫자만 입력가능하다
    - NUMBER(DECIMAL) 소수점과 같이 숫자와 점(.)이 입력가능하다
    - NUMBER(COMMA) 숫자만 입력 가능하며 자동으로 콤마(,)가 3자리마다 찍힌다. 앞글자 0은 모두 제거된다

- Place Hodler Color `string` `optional` #ff0000과 같이 입력하며, place holder의 색깔이다. defuat는 #666666이다
- Max Length `number` `optional` 최대 입력가능한 글자수 이다 default는 제한이 없다
    

#### Hidden
Block Contition 에 따라 