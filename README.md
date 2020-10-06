# Hugo Start
## Hugo를 사용하는 이유
먼저, Github page를 활용한 정적 페이지로 문서화하는 이유부터 말해야 할 것 같다. 첫 째는 모든 개발관련 공부 및 글을 Github에서 관리하려고 한다. 여기서 주제가 다른 글들을 여러 repository로 관리하다보니 불필요한 시간낭비와 정리하기가 매우 어려웠다. 이를 차라리 한 곳에서 관리하고 싶었다. 둘 째는 개발을 하면서 또는 관련 공부를 하면서 수 많은 정리글을 적게 되는데, 이를 카테고리화할 수 있는 블로그 플랫폼을 찾을 수 없었다. 물론 태깅, 시리즈 등등 여러 기능을 제공하는 플랫폼은 있지만 보기가 불편하다. 위키처럼 구조화된 메뉴를 기반하고 내부에서 검색이 가능한 플랫폼을 찾고 있는데, 이에 적합한 것이 github를 활용한 정적페이지였다. 그 중에서도 빌드가 가장 빠르다는 Hugo를 선택했다.

Hugo의 단점은 진입장벽이다. 한글 문서가 많이 없다. 그리고 자동 배포화 등등 여러 기능을 직접 적용해야 하기 때문에 그 방법을 찾는 것도 삽질하는 것도 많은 시간이 소요된다. 하지만 한 번 환경을 구성해놓으면 글을 작성하는데 집중할 수 있을 것이다. 그리고 여러 다양한 기능들을 필요에 맞게 추가할 수 있고, 관리할 수 있다.

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
- `hugo server`로 로컬 서버 실행했을 때, `ERROR 2020/10/05 06:24:52 Error: listen tcp 127.0.0.1:1313: socket: too many open files in system` 오류
    - <https://superuser.com/questions/827984/open-files-limit-does-not-work-as-before-in-osx-yosemite>
        - 위 게시글의 첫 번째 답변 그대로 따라하면 해결된다.
- github의 Github Actions로 기존 배포 설정으로 배포했을 때, postcss를 찾지 못하는 오류


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
