# Self Study of safe-eye

제가 참여한 safe-eye 프로젝트에 대한 이해도를 증진시키기 위해 따로 진행한 "프로젝트에 대한 전반적인 분석 내용들"을 정리한 레포지토리입니다.

# 해야 할 내용들

## 1. 프로젝트 구조 분석
폴더 및 파일 구조 이해
각 앱(예: accounts, chat, media, alarm)의 역할과 기능 파악
config 폴더의 설정 파일(settings.py, urls.py) 분석
manage.py와 requirements.txt의 중요성 이해

## 2. 모델 분석
데이터베이스 모델링
각 앱의 models.py 파일을 통해 데이터 모델 구조 파악
예: accounts 앱의 사용자 모델, chat 앱의 채팅 모델, alarm 앱의 알림 모델
관계 분석: ForeignKey, ManyToManyField 등 관계 설정 이해
데이터 유효성 검사 및 제약 조건 확인

## 3. API 설계 분석
Django REST Framework 설정
각 앱의 serializers.py 파일을 통해 데이터 직렬화 방법 이해
views.py에서 API 엔드포인트 구현 방식 분석
URL 라우팅(urls.py)에서 엔드포인트 구조 및 접근 방식 확인

## 4. 비즈니스 로직 분석
주요 기능 및 흐름 이해
사용자 인증 흐름: 로그인, 로그아웃, 사용자 등록 기능 분석
비디오 업로드 및 분석 흐름: 비디오 파일 처리 과정 및 PySlowFast 모델과의 연동 이해
이상 행동 감지 로직 및 그 결과 처리 방식 분석

## 5. 외부 서비스 연동 분석
AWS S3 연동
settings.py에서 S3 설정 확인 (스토리지 관련)
파일 업로드 및 다운로드 과정에서 S3와의 상호작용 이해
PySlowFast 모델 API 연동
API 호출 및 응답 처리 로직 분석
비디오 분석 결과를 어떻게 처리하고 저장하는지 확인

## 6. 사용자 인터페이스 분석
프론트엔드와의 상호작용
프론트엔드에서 API 엔드포인트를 호출하는 방식 (예: Next.js 컴포넌트)
사용자 입력을 처리하는 방법 (비디오 업로드, 사용자 입력)

## 7. 오류 처리 및 예외 관리
예외 처리 전략 이해
API 호출 시 오류 처리 방식 (예: 잘못된 요청, 인증 실패 등)
로그 기록 및 디버깅 방법 확인

## 8. 테스트 및 배포 전략
테스트 코드 분석
각 앱의 tests.py에서 테스트 케이스 및 테스트 커버리지 확인
배포 설정 이해
Dockerfile 및 CI/CD 파이프라인 구성 이해

## 9. 성능 최적화 및 보안
성능 고려 사항
데이터베이스 쿼리 최적화 (예: select_related, prefetch_related)
비디오 처리 성능 최적화 방법
보안 고려 사항
사용자 인증 및 권한 관리 전략 확인
S3 버킷의 CORS 설정 및 보안 설정 분석
