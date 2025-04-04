# 태스크 #001: Cline 규칙 시스템 개선

## 태스크 정보
- **태스크 번호**: #001
- **태스크 이름**: Cline 규칙 시스템 개선
- **생성일**: 2025-03-25
- **상태**: 진행 중
- **우선순위**: 높음
- **담당자**: luke
- **예상 소요 시간**: 2시간

## 태스크 목적
Cline의 규칙 시스템을 개선하여 더 효율적이고 관리하기 쉬운 구조로 재구성합니다. 현재의 다국어 지원 및 복잡한 파일 구조를 단순화하고, JSON 기반의 새로운 규칙 시스템을 구축하여 토큰 사용량을 최적화합니다.

## 실행 단계
1. **.clinerules 백업 및 전환**
   - [X] 현재 .clinerules 파일 백업 
   - [X] 프로젝트 개발 가이드로 내용 변환하여 레퍼런스 : docs\architecture\project-guide.md   

2. **룰 모드 프로세스 정의**
   - [X] 룰 모드의 프로세스 정의 완료
     * 규칙 검토 및 제안
     * 개발자 승인 후 버전 관리
     * 규칙 업데이트 및 테스트
     * 검증 및 확정
   - [ ] 버전 관리 시스템 구현
     * 버전별 규칙 보관 (agents-rules/alpha/versions/)
     * 변경 내역 기록
     * 롤백 지원

3. **규칙 편집 시스템 개발**
   - [ ] 실시간 JSON 업데이트 스크립트 통합
   - [ ] 규칙 버전 관리 시스템 구축
   - [ ] 효과 분석 시스템 개발
   - [ ] 롤백 기능 구현

4. **테스트 및 문서화**
   - [ ] 새로운 규칙 시스템 테스트
   - [ ] 사용자 문서 작성
   - [ ] PR 준비

## 참고 자료
- .clinerules - 현재 Cline 규칙 문서
- agents-rules/alpha/project-rules.json - Cursor 스타일 규칙 시스템
- scripts/doc-watcher.cjs - 실시간 업데이트 스크립트

## 진행 상황
- 태스크 계획 수립 완료
- 기존 다국어 지원(.ko.json, .md) 제거 결정
- JSON 형식으로 통일하여 토큰 사용량 최적화 계획

## 메모
- 규칙 시스템은 JSON으로 단일화하되, 필요시 마크다운으로 변환 가능하도록 구현
- 버전 관리는 Git 기반으로 구현하여 변경 이력 추적 용이하게 함
- 효과 분석은 예상 Q&A 생성 및 테스트를 통해 검증

## Rule 모드 프로세스
1. **규칙 검토 및 제안**
   - 현재 영문 JSON 규칙 분석
   - 가독성과 최적화 관점에서 개선점 도출
   - 개선 제안 작성
   
2. **개발자 승인 후 버전 관리**
   - 버전 번호 증가 (v1.0.0 → v1.1.0)
   - 이전 버전 보관:
     * agents-rules/alpha/versions/v1.0.0/project-rules.json
     * 각 버전별 변경 내역 기록
   - 검증용 시나리오 작성:
     * 예상 질의 목록
     * 각 질의별 기대 반응
   
3. **규칙 업데이트 및 테스트**
   - 새 버전의 규칙으로 업데이트
   - 새 세션에서 테스트 진행 요청
   
4. **검증 및 확정**
   - 개발자가 새 세션에서 검증
   - 결과에 따라:
     * 실패 시 → 이전 버전으로 롤백
     * 성공 시 → 새 버전 확정
