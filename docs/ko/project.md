# Theme

테블릿 혹은 가로 모드의 경우와 마찬가지로 theme도 자동으로 배핑될 수 있다
Project Edit > App Decoration > Use Theme 스위치를 on 하면

앱은 Jevil.get('THEME')의 값을 참조하여, 그 테마에 맞는 스캐치 노드를 찾는다
해당 테마에 해당하는 스케치 노드가 없다면 기본을 보여준다

Jevil.get('THEME')가 white 혹은 dark라면

    - myscreen
    - myscreen-theme-white
    - myscreen-theme-dark


로 대체 된다

tablet 혹은 landscape와의 혼합

    - myscreen-tablet-theme-white
    - myscreen-tablet-theme-dark
    - myscreen-landscape-theme-white
    - myscreen-landscape-theme-dark
    - myscreen-tablet-landscape-theme-white
    - myscreen-tablet-landscape-theme-dark

앱에서 테마를 변경하고 싶으면 Jevil.save('THEME' ,'white') 혹은 기본 테마로 돌아가고 싶으면
Jevil.remove('THEME') 로 한다