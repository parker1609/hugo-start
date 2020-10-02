# Hugo Start

## 1. Hugo Quick Start
- 참고: <https://gohugo.io/getting-started/quick-start/>

## 2. Hosting Github Page
3번에서 github actions를 사용하면 자동으로 github page에 빌드가 된다.

## 3. CI/CD 환경 구축
- github actions 사용
    - travis CI와 같은 다른 무료 CI보다 속도가 빠르다.
    - 더 다양한 설정을 할 수 있다.
    - github 자체에서 제공하기 때문에 호환성이 더 좋을 듯하다.(hugo 자체도 github에서 사용하기 때문)
- 참고사항
    - [2. Github Action으로 hugo블로그 자동 배포하기](https://velog.io/@ceres/Github-Action%EC%9C%BC%EB%A1%9C-hugo%EB%B8%94%EB%A1%9C%EA%B7%B8-%EC%9E%90%EB%8F%99-%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0)

### Issues
- 위 참고사항에서 명시된 링크에서 제공한 yml 파일을 빌드 설정을 했을 때, theme가 동작하지 않는다.
    - 개발자 모드로 보면, css 파일은 비워져 있고 js 파일 자체는 없었다.
    - 해결방법: config.toml 파일의 base URL이 현재 github page에 올라가는 실제 URL과 달라서 해당 URL에 올리지 못한 것으로 예상한다.

## 4. Docsy 테마 사용하기
- Doscy
    - Hugo 테마 중 star 수도 TOP 5안에 들고, 개인 홈페이지도 만들어서 문서화하며 잘 관리되어있는듯 하다.
    - 기본적인 문서화 기능을 제공한다.
### Issues
- 잘못 설치한 git submodule 삭제하기
    - <https://jjeong.tistory.com/1345>
    - `fatal: Please stage your changes to .gitmodules or stash them to proceed` 와 같은 에러가 나오면 에러 메시지 대로 `git add .`해서 변경사항을 적용한다.


## Hugo Project
### 구성요소
#### 메인 Hugo 페이지
- 여러 서브 Hugo 페이지의 링크를 모아놓음
- 자기소개(이력서)
- 링크버켓

#### 서브 Hugo 페이지
- 깃허브에서 관리하는 문서화 레포지토리
    - TIL
    - Web 백과사전
    - PS
    - ...

### 요구사항
- Github Page에 호스팅한다.
- 특정시간에 자동으로 빌드 및 배포한다.
    - 변경사항이 있으면 자동으로 commit을 한 후 빌드 및 배포를 시작한다.
    - 모든 Hugo 페이지들이 동일하게 적용된다.
