Async vs Defer
https://html.spec.whatwg.org/#attr-script-defer

https://html.spec.whatwg.org/#script-processing-model




이 문서가 정리가 잘됨.
https://ko.javascript.info/script-async-defer

1. script는 html 문서의 완벽한 동작을 위해 script를 다 로드한 후에 html 처리를 계속한다.
-> 완벽한 동작이란..?

그래서 async, defer 이전에는..
스크립트를 문서의 하단에 둠.

2. async, defer의 등장
async, defer - 비동기

다른점
async 문서 로드에 상관없이 js 파일이 로드 되면 바로 실행.
defer DocumentLoadded Event 에서????
