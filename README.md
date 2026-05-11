# 프로젝트 소개

Spring Boot 기반 일정 관리 API 프로젝트입니다.  
프로젝트 실행 오류 수정, Argument Resolver 등록, 코드 리팩토링, Validation 적용, N+1 문제 해결, 테스트 코드 및 서비스 로직 수정을 진행했습니다.

---

# 구현 내용

## Lv 0. 프로젝트 세팅 및 에러 분석

- JWT 설정값 누락으로 인한 애플리케이션 실행 오류 해결
- `application.yml`에 `jwt.secret.key` 추가

---

## Lv 1. Argument Resolver 적용

- `AuthUserArgumentResolver` Bean 등록
- `WebMvcConfigurer#addArgumentResolvers()`를 통한 Resolver 등록

---

## Lv 2. 코드 개선

### Early Return 적용
- 중복 이메일 검사 이후 비밀번호 인코딩 수행하도록 수정

### 불필요한 if-else 제거
- 중첩된 `else` 제거

### Validation 적용
- 비밀번호 검증 로직을 DTO Validation으로 이동
- `@Pattern`, `@Valid` 적용

---

## Lv 3. N+1 문제 해결

- `fetch join` → `@EntityGraph` 방식으로 변경
- 정렬 조건 추가

---

## Lv 4. 테스트 코드 수정

- 실제 서비스 로직에 맞게 예외 타입 수정
- 테스트 메서드명 수정
- null 상황에 대한 서비스 방어 로직 추가