# Micro Service Architecture

## Q. 본 프로젝트의 목적은 무엇인가?

### A. 경험한 프로젝트에서의 문제점들을 파악 및 정리하므로서 기술 스택 향상과 이슈 해결 능력을 키우는데 목적이 있습니다.

1. 첫 번째 문제점 - 모놀리틱 프로젝트
* 마이크로 서비스 아키텍처 적용

2. 두 번째 문제점 - 늘어나는 Entity 및 DTO 관리
* inner class 및 빌더 패턴 적용

3. 세 번째 문제점 - Quartz로 대용량 처리 시 Job 성공, 실패 및 관리
* 스프링 배치 및 Quartz 스케줄러 적용

4. 네 번째 문제점 - 이메일 및 문자 알림 전송 시의 병목 현상과 전송 성공, 실패 관리
* Message Queue를 이용한 비동기식 메시지 처리


# 아키텍처

![image](https://user-images.githubusercontent.com/19419438/160290362-db3e08f3-e246-465b-a18f-a24aecfc07ca.png)