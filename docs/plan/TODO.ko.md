# 구현 TODO

영문판: [TODO.en.md](TODO.en.md). 리프 항목 하나 ≈ GitHub 이슈 하나. 괄호 안은 브랜치 이름.

```
Stock Briefing Agent
├── S0. 준비 (11/23, Sprint 1 첫 세션)
│   ├── CLAUDE.md 작성 (placeholder → 실제 규칙)
│   ├── Python 프로젝트 뼈대: pyproject, src/briefing/, tests/, `briefing run` CLI 진입점
│   ├── config 파일: 관심 종목, 종목별 섹터 ETF·별칭, 임계값
│   ├── dingo 연결 확인 + Qwen 정확한 태그 확인 → README stack 표 채우기
│   └── Telegram 봇 생성 + 메시지 전송 테스트 (토큰은 .env)
│
├── Sprint 1 (11/23 – 12/13)
│   ├── G1 등락 측정                    (feat/g1-measure-move)
│   │   ├── 가격 수집: 일봉 + 프리/애프터마켓 (yfinance)
│   │   ├── 지표 계산: 등락률, 갭, 시간외 등락, 거래량 vs 20일 평균
│   │   ├── 추세 라벨: 오늘 등락 × 추세, 변동성 정규화, weak 표시, 연속 일수
│   │   └── 테스트: 고정 데이터로 라벨 케이스 검증
│   ├── G2 시장 vs 종목 분리            (feat/g2-market-split)
│   │   ├── 시장(SPY/QQQ)·섹터 ETF 등락 수집
│   │   ├── 시장 / 섹터 / 종목 고유 몫 분해
│   │   └── 수치 테스트
│   ├── G3 이슈 수집                    (feat/g3-gather-issues)
│   │   ├── 뉴스: yfinance .news + RSS (Yahoo, Nasdaq, Google News)
│   │   ├── 공시: SEC EDGAR (User-Agent 설정)
│   │   ├── 애널리스트 등급 변경 + 실적 일정/서프라이즈
│   │   ├── 시간 창 필터 + 중복 제거 + 이름/티커/별칭 매칭 표시
│   │   └── 실행별 수집 로그
│   ├── 매일 데이터 수집                (feat/daily-collect)
│   │   ├── 하루 1회 원본 스냅샷 로컬 저장 (data/raw, 커밋 안 함)
│   │   └── launchd/cron 예약 실행 + 실패 시 재시도
│   ├── 중간 산출물: G1–G3만으로 만든 Markdown 리포트 (숫자 + 이슈 목록, LLM 없음)
│   └── 체크포인트 (12/14): 진행 상황 슬라이드 1장 + 발표
│
├── Sprint 2 (12/21 – 1/11)
│   ├── G4 관련성 분류                  (feat/g4-classify)
│   │   ├── 분류 기준표(rubric) + 종목 프로필 입력 형식
│   │   ├── Qwen 프롬프트 + JSON 출력 {category, quote, confidence}
│   │   ├── 자동 검사: 인용문 존재, 이름 매칭, 두 번 묻기, JSON 형식 → 실패 시 uncertain
│   │   └── dingo 장애 시 로컬 모델 대체
│   ├── G5 브리핑 작성·전송             (feat/g5-brief)
│   │   ├── Markdown 렌더링 (숫자는 코드가 삽입)
│   │   ├── 숫자 검사 (모델이 쓴 숫자 거부)
│   │   └── Telegram 축약본 전송
│   ├── G6 품질 측정                    (eval/g6-quality)
│   │   ├── 수집 뉴스 150–200건 직접 라벨링 (data/eval, 커밋함)
│   │   ├── 정밀도/재현율, 혼동 행렬, 오류 유형
│   │   ├── Qwen 3.6 35B vs 작은 로컬 모델 비교
│   │   └── (선택) 원인 추정 실험
│   └── Demo Day (1/11)
│       ├── README 설치/실행/데모 섹션 완성
│       ├── 데모 시나리오 (10분)
│       └── ERK 보고서 (AI 사용 선언 포함, 세션 로그 근거)
│
└── 계속할 것
    ├── 세션마다 세션 로그 + PR
    └── README Progress / Goals 상태 업데이트
```
