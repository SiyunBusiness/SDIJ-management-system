# 전사고 학생 관리 시스템 - TODO

## Phase 1: DB 스키마 설계 + 마이그레이션
- [x] users 테이블 확장 (role: admin/parent/student/teacher)
- [x] user_profiles 테이블 (학생/학부모 연결, 학년, 반 등)
- [x] subscriptions 테이블 (학부모 구독 신청, pending/approved/rejected)
- [x] weeks 테이블 (주차 정보, 시작일/종료일, 1차/2차 제출 마감일)
- [x] submissions 테이블 (학생 제출 기록, 동영상 파일 키, 제출 차수)
- [x] video_access_links 테이블 (선생님용 QR/링크, 만료일 7일)
- [x] DB 마이그레이션 실행

## Phase 2: 백엔드 API 구축
- [x] 역할 미들웨어 (adminProcedure, teacherProcedure, studentProcedure, parentProcedure)
- [x] 구독 신청 API (학부모: create subscription)
- [x] 구독 승인/반려 API (관리자: approve/reject)
- [x] 주차 관리 API (주차 생성, 조회, 활성화)
- [x] 과제 제출 API (학생: 동영상 업로드, S3 저장)
- [x] 1차 제출 완료 시 2차 면제 자동 처리 로직
- [x] 선생님용 접근 링크 생성 API (7일 만료)
- [x] 선생님 피드백 API
- [x] 성취도 통계 API (주차별 제출률, 완료율)
- [x] 관리자 사용자 목록 API
- [x] 관리자 알림 (구독 승인/반려 시 notifyOwner)

## Phase 3: 글로벌 레이아웃 및 라우팅
- [x] 글로벌 테마 설정 (elegant Navy & Gold 팔레트, Noto Sans KR)
- [x] AppLayout 컴포넌트 (역할별 사이드바 메뉴)
- [x] 역할별 라우팅 (로그인 후 자동 리다이렉트)
- [x] 인증 가드 (미인증 시 로그인 페이지로)
- [x] 랜딩 페이지 (서비스 소개, 역할별 기능 안내)
- [x] ProfileSetup 페이지 (최초 로그인 시 역할 설정)

## Phase 4: 학생/학부모 대시보드 및 과제 제출
- [x] 공유 대시보드 컴포넌트 (학생/학부모 동일 UI)
- [x] 현재 주차 진행 상황 표시 (D-day, 마감일)
- [x] 과제 제출 현황 카드 (1차/2차 분리)
- [x] 동영상 업로드 컴포넌트 (학생만 활성화, 학부모 숨김)
- [x] 1차/2차 제출 기한 표시 및 면제 상태 렌더링
- [x] 주차별 성취도 바 차트 (Recharts)
- [x] 제출 완료율 프로그레스 바

## Phase 5: 선생님 대시보드 및 QR/링크 시스템
- [x] 선생님 대시보드 (학생별 제출 현황 그룹핑)
- [x] 동영상 접근 QR코드 생성 (qrcode 패키지)
- [x] 7일 만료 스트리밍 링크 생성 및 표시
- [x] VideoAccessPage (만료된 링크 접근 차단 처리)
- [x] 피드백 입력 다이얼로그

## Phase 6: 관리자 대시보드 및 사용자 관리
- [x] 관리자 대시보드 (전체 현황 요약 카드)
- [x] 구독 신청 목록 (pending 상태 필터링)
- [x] 승인/반려 버튼 및 처리 UI
- [x] 전체 사용자 목록 및 역할 변경 다이얼로그
- [x] 주차 생성/활성화 UI

## Phase 7: 성취도 시각화 및 UI 완성
- [x] 주차별 성취도 그래프 (Recharts BarChart, 색상 구분)
- [x] 과제 제출 완료율 프로그레스 바
- [x] TypeScript 에러 0개 달성

## Phase 8: 테스트 및 배포
- [x] 21개 Vitest 테스트 작성 및 통과 (auth, admin, weeks, submissions, videoLinks, subscriptions, users)
- [x] 체크포인트 저장
- [x] 배포 (Publish 버튼 클릭 - 사용자가 UI에서 직접 진행)

## 이메일/비밀번호 자체 로그인 시스템
- [x] local_credentials 테이블 DB 스키마 추가 및 마이그레이션
- [x] 백엔드 register/login/logout API (bcrypt 해싱, JWT 세션)
- [x] 프론트엔드 로그인 페이지 (/login) 구현
- [x] 프론트엔드 회원가입 페이지 (/register) 구현
- [x] 기존 Manus OAuth와 자체 로그인 병행 지원
- [x] 학생 임시계정 생성 (student@test.com)
- [x] 학부모 임시계정 생성 (parent@test.com)

## 학생 과제 제출 기능 개선
- [x] 학생 대시보드 - 워크북/테스트/주간지 제출 칸 UI 구현
- [x] 파일 선택 → S3 업로드 → DB 저장 전체 플로우 동작 (presigned URL 방식)
- [x] 1차(워크북/테스트) / 2차(워크북/테스트/주간지) 제출 구분 표시
- [x] 제출 완료 상태 시각적 표시 (완료/미제출 배지)

## 동영상 업로드 네트워크 오류 수정
- [x] presigned URL 방식 → 서버 경유 multipart 업로드 방식으로 전환
- [x] 업로드 API 엔드포인트 수정 및 테스트

## 과제 제출 및 평가 시스템
- [x] submissions 테이블 status 필드 추가 (approved/resubmit enum 추가, DB ALTER TABLE 완료)
- [x] 선생님 평가 API (evaluate 프로시저: approved/resubmit + 피드백)
- [x] 선생님 대시보드 - 평가 다이얼로그 (완료/다시제출 버튼)
- [x] 학생 대시보드 - 미제출/제출(검토중)/완료/다시제출 4가지 상태 표시
- [x] 제출 상태일 때 '선생님의 확인을 기다리는 중입니다.' 메시지 표시
- [x] 다시제출 상태일 때 재업로드 버튼 활성화 (선생님 피드백 표시 포함)

## 과제 제출 UI 개편 및 미제출 탭
- [x] 1,2차 분리 카드 → 5개 통합 제출칸 (워크북1/2, 테스트1/2, 주간지) 단일 카드로 변경
- [x] 현재 제출 기간(1차/2차) 표시 - 현재 어느 기간인지 배지로 표시 (헤더 배지 + 각 행 '현재 기간' 태그)
- [x] 면제(exempted) 상태 표시 제거 (StatusBadge에서 면제 케이스 삭제)
- [x] '나의 미제출 과제' 탭 추가 - 미제출/다시제출 상태 과제 목록 표시 (주차별 그룹핑, 미제출 카운트 배지)

## UI 및 기능 개선 (2026-05-07)
- [x] 사이드바 내비게이션 복구 - wouter Link 컴포넌트로 변경 (계정 설정 메뉴 추가 포함)
- [x] submissions 테이블 isLate 컨럼 추가 + DB 마이그레이션
- [x] users 테이블 address 컨럼 추가 + DB 마이그레이션
- [x] 과제 제출 버튼 항상 활성화 (기한 지나도 지연 제출 허용)
- [x] 지연 제출 상태 표시 - 제출 시 isLate 쪼러에 저장, 학생 UI에 '지연' 배지 표시
- [x] 계정 설정 페이지 구현 (react-hook-form + zod + tRPC, /settings 라우트)
- [x] updateProfile tRPC mutation에 address 필드 추가 (users.address + user_profiles 동시 업데이트)

## 주차 관리 시스템 전면 개편 (2026-05-07)
- [x] weeks 테이블에 year, semester, grade, subject 컨럼 추가 + DB 마이그레이션
- [x] weeks 라우터 - 일괄 생성(bulkCreate) 프로시저: 시작일 기준 자동 마감일 계산(+3일 1차, +5일 2차), 여러 주차 한번에 생성
- [x] weeks 라우터 - 삭제(deleteGroup) 프로시저: 관련 submissions 포함 전체 삭제
- [x] weeks 라우터 - 학생용 조회 프로시저: startDate <= 현재시간인 주차만 반환
- [x] 관리자 WeeksPage 전면 개편: 년도/학기/학년/과목/열주차수/시작일 입력 폼 + 그룹 삭제 경고 다이얼로그
- [x] 학생 대시보드 - 아코디언 주차 목록 페이지(StudentSubmissions.tsx) 신규 생성 (현재 주차 기본 펼침, 과거 주차 클릭 열람 가능)
- [x] 학생 대시보드 - 년도/학기/학년/과목/주차 형식 표시 (StudentSubmissions.tsx)
- [x] 미제출 탭 → 사이드바 메뉴로 이동 (StudentUnsubmitted.tsx + /student/unsubmitted 라우트)

## 관리자 회원 등록 및 로그인 방식 변경 (2026-05-07)
- [x] local_credentials 테이블에 loginName/loginRole/loginPhone 컬럼 추가 + DB 마이그레이션
- [x] 로그인 로직 변경: 이름+역할(student/parent)+전화번호+비밀번호 조합으로 인증
- [x] 관리자 계정 생성 API (admin.createUser): 이름/역할/학교명/전화번호 입력, 기본 비밀번호 설정
- [x] db.ts에 createLocalUser 헬퍼 함수 추가
- [x] 로그인 페이지 UI 변경: 이름/역할/전화번호 입력 필드, 이메일 필드 제거
- [x] 회원가입 페이지 제거 → 관리자 문의 안내 페이지로 교체 (Manus OAuth 로그인 유지)
- [x] 관리자 사용자 관리 탭 - 사용자 추가 버튼 (직접입력 다이얼로그 + 엑셀 일괄 등록 탭 안내 표시)

## 과목별 주차 UI 개선 (2026-05-08)
- [x] weeks 라우터 - listAllForStudent 프로시저 추가 (시작일 제한 없이 전체 주차 반환)
- [x] 관리자 WeeksPage - 주차 목록을 과목별 탭(전체/미적/기하/대수/확통)으로 분리
- [x] 관리자 WeeksPage - 과목별 주차 수 카운트 표시
- [x] 학생 StudentParentDashboard - 과목별 탭 필터(전체/미적/기하/대수/확통) 추가
- [x] 학생 StudentParentDashboard - 주차 카드 아코디언 방식으로 재작성 (과목 배지, 마감일, 제출 현황 요약)
- [x] 학생 StudentParentDashboard - 각 주차 내 5개 과제 목록 표시 (업로드 버튼 포함)

## 과목별 독립 활성 주차 지원 (2026-05-08)
- [x] weeks 라우터 setActive - 같은 과목 내에서만 기존 활성 주차 비활성화 (다른 과목은 유지)
- [x] 학생 대시보드 - 과목별 활성 주차 복수 표시 지원 (active API 대신 listAllForStudent 기반으로 과목별 활성 주차 표시)

## 수강 과목 관리 및 과제 제출 탭 개선 (2026-05-08)
- [x] DB: user_profiles에 subjects 컨럼(JSON 배열) 추가 및 마이그레이션
- [x] 백엔드: users.myInfo에 subjects 포함, admin.getStudentSubjects/updateStudentSubjects 추가
- [x] 백엔드: weeks.listForStudent/listAllForStudent에 학생 수강 과목 필터 적용
- [x] 계정 설정 페이지 - 학생인 경우 수강 과목 읽기 전용 표시
- [x] 관리자 사용자 관리 - 학생 행에 '과목' 버튼 및 수강 과목 수정 다이얼로그 추가
- [x] 과제 제출 탭 - 과목별 탭 분류 추가 (수강 과목만 표시)
- [x] 과제 제출 탭 - 첫 주차부터 오름차순 정렬
- [x] 과제 제출 탭 - 미래 주차(시작일 미도래) 자물쇠 아이콘 + '예정' 배지로 잠금 처리
- [x] 과제 제출 탭 - 진행 중 주차 맨 위 고정, 나머지 오름차순

## 학년 필터 및 계정 설정 학년 기본값 수정 (2026-05-08)
- [x] weeks.listForStudent/listAllForStudent - 학생 프로필의 grade 기반 필터링 추가
- [x] 계정 설정 학년 드롭다운 - 저장된 학년 값이 기본 선택되도록 수정 (Controller key prop 추가)

## 주차 일괄 등록 요일 선택 기능 (2026-05-08)
- [x] bulkCreate 다이얼로그 - 1차 마감 요일 선택(일~토) 드롭다운 추가
- [x] bulkCreate 다이얼로그 - 2차 마감 요일 선택(일~토) 드롭다운 추가
- [x] 1주차 시작일 기준으로 선택한 요일까지의 날짜를 계산하여 각 주차 마감일 자동 설정
- [x] 나머지 주차들도 동일 요일 기준으로 +7일씩 자동 계산 (백엔드 calcDeadlineOffset 함수)
- [x] 미리보기 섹션에 선택한 요일 기준 1차/2차 마감일 실시간 표시

## 관리자 과제 검토 기능 추가 (2026-05-08)
- [x] AppLayout admin 사이드바에 "과제 검토" 탭 추가 (/admin/review)
- [x] AdminDashboard.tsx에 ReviewPage 컴포넌트 추가 (주차 선택 + 학생별 제출 목록)
- [x] QR/링크 생성, 피드백 작성, 완료/다시제출 평가 다이얼로그 포함
- [x] AdminDashboard 라우팅에 /admin/review 경로 추가

## 과제 검토 주차 선택 UI 개선 (2026-05-08)
- [x] ReviewPage 주차 선택을 년도/학년/학기/과목/주차 순서의 단계별 드롭다운 필터로 변경 (연계 필터링, 선택 요약 표시)

## 전체 UI 무채색 미니멀 디자인 개편 (2026-05-08)
- [x] index.css CSS 변수 - 흰 배경 + 검정/회색 무채색 팔레트로 전환 (라이트 테마)
- [x] AppLayout 사이드바 - 역할 배지 무채색 전환
- [x] 로그인 페이지 - 좌측 검정 브랜딩 + 우측 흰 배경 양식 미니먀 디자인
- [x] 향후 개발에서도 무채색 미니먀 디자인 유지 (프로젝트 지침 업데이트)

## 비밀번호 변경 기능 (2026-05-08)
- [x] 백엔드: localAuth.changePassword 프로시저 추가 (현재 비밀번호 확인 + 새 비밀번호 해싱 저장)
- [x] 프론트엔드: Settings.tsx에 비밀번호 변경 카드 추가 (현재/새/확인 입력 폼)
- [x] 로컬 계정이 없는 경우(Manus OAuth 전용) 비밀번호 변경 섹션 숨김 처리
- [x] Vitest 테스트 작성 (changePassword 성공/실패 케이스)

## 주차 자동 활성화/비활성화 (2026-05-08)
- [x] db.ts: syncWeekActiveStatus() 함수 추가 (startDate <= now → isActive=true, secondDeadline < now → isActive=false, 과목별 독립 처리)
- [x] weeks 라우터 조회 프로시저(list, active, listForStudent, listAllForStudent)에 syncWeekActiveStatus() 호출 추가
- [x] Vitest 테스트 작성 (자동 활성화/비활성화 케이스)

## 학기/학년 순서 전수 수정 (2026-05-08)
- [x] server/routers/weeks.ts: bulkCreate title 생성 로직 수정 (${semester}학기 ${grade}학년 → ${grade}학년 ${semester}학기)
- [x] server/routers/weeks.ts: bulkCreate 폼 UI 학기→학년 순서 수정 (AdminDashboard 폼 레이블 순서)
- [x] client/src/pages/AdminDashboard.tsx: 주차 목록 표시 텍스트 수정 (이미 수정됨 확인)
- [x] client/src/pages/AdminDashboard.tsx: bulkCreate 폼에서 학기 선택이 학년보다 먼저 나오는 순서 수정
