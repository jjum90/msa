# MicroServices Architecture

## Q. 본 프로젝트의 목적?

## A. 경험한 프로젝트에서의 문제점들을 파악 및 정리하므로서 기술 스택 및 이슈 해결 능력을 향상

###1. 의존성과 결합도

       1-1. 프로젝트의 규모가 커지고 사용자의 트래픽이 많이 늘어나는 상황 또한 요건 기능 추가 및 간금 버그 수정을 하더라도 전체 서비스를 빌드해서 묶고 다시 배포
      
       1-2. 모놀리틱 구성된 서비스로 인해 서비스간의 결합도 의존도가 높아 유지보수가 어려우며 하나의 서비스 장애가 생기면 전체적인 장애로 퍼져나가 운영을 중단

* 마이크로 서비스 아키텍처 적용

###2. Entity 및 DTO

      2-1. 개발자 인원 수가 늘어나고 요건 기능 추가에 따라 늘어나는 Entity 및 DTO 가 기하급수적으로 증가
   
      2-2. 하나의 Entity에 다수개의 DTO가 의존하고 있어 개발자가 파악하기 쉽지 않으며 DTO 하나를 수정해도 여러개를 같이 수정

      2-3. DTO Validation 체크를 비지니스 로직 안에서 소스 결합도가 높고 각 필드의 Validation 정보를 개발자가 알기 힘듬 

* inner static class, 빌더 패턴, @Valid annotation 적용

###3. 세 번째 문제점 - Quartz로 대용량 처리 시 Job 성공, 실패 및 관리

      3-1. NoSQL 사용으로 인해 Batch를 쓰지 못하고 Quartz를 사용해서 일괄 처리를 하다보니 chunk 및 paging 단위가 아닌 모든 데이터를 가져와서 하므로 오버헤드 발생
   
      3-2. 스케줄링을 통해서 일괄 데이터를 관리하다 보니 데이터가 중간에 실패되어도 재처리 불가

* 스프링 배치 및 Quartz 스케줄러 적용

###4. 네 번째 문제점 - 이메일 및 문자 알림 전송 시의 병목 현상과 전송 성공, 실패 관리

      4-1. 문자 및 이메일 발송 시 비동기 처리 및 batch 작업으로 전송 결과를 처리 3-1과 마찬가지로 데이터가 유실될 가능성이 존재

* Message Queue를 이용한 비동기식 메시지 처리


# 아키텍처

![image](https://user-images.githubusercontent.com/19419438/160290362-db3e08f3-e246-465b-a18f-a24aecfc07ca.png)
