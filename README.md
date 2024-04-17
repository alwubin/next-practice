# next-practice

## Troubleshooitng #1
### 🔍문제 정의 
<img width="1180" alt="image" src="https://github.com/alwubin/next-practice/assets/135022491/406e33c3-b5f3-4da8-b87a-82e2837c5517">
원인은 SSL/TLS 인증서가 만료되었기 때문에 Next.js 서버 개발 중에 `code: 'CERT_HAS_EXPIRED'`가 발생했다.
근데 아무리 인증서들을 확인해도 만료된 인증서는 없었기 때문에 인증서 갱신하는 방법은 할 수 없었다.

### ✅문제 해결 과정
- `npm config set strict-ssl false` : 인증서 검증 옵션을 비활성화하는 명령어
해결되지 않았다.
- `process.env.NODE_TLS_REJECT_UNAUTHORIZED = '0';` : 직접 파일 내에 추가하여 인증서 검증 옵션을 비활성화 하는 코드
해결되었지만, 단 프로덕션 환경에서는 보안상의 이유로 개발 환경에서만 사용하는 것이 좋다.
