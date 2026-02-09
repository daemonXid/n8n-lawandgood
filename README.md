# LawAndGood

> AI 기반 소송금융(Litigation Finance) 투자 적합 뉴스 자동 분석 시스템

## Live Dashboard

**https://daemonxid.github.io/n8n-lawandgood/**

## System Architecture

```
Naver News API ──▶ n8n (수집) ──▶ Google Sheets ──▶ 정적 대시보드
                   n8n (분석) ──▶ Gemini AI ──┘       (GitHub Pages)
```

## Tech Stack

| Layer | Technology |
|:---|:---|
| **Automation** | n8n (Self-hosted, Hetzner VPS) |
| **LLM** | Google Gemini 2.0 Flash Lite |
| **Database** | Google Sheets |
| **Frontend** | HTML + Tailwind CSS (JSONP) |
| **Hosting** | GitHub Pages |
| **News Source** | Naver News Search API |

## Workflows

### 1. News Crawling (1시간 간격)

- 7개 키워드 기반 뉴스 자동 수집
- 키워드: 소송, 손해배상, 집단소송, 공동소송, 피해자, 피해보상, 피해구제
- Naver News API → 데이터 정리 → Google Sheets 저장

### 2. AI Analysis (2분 간격)

- 미분석 기사 5개씩 배치 처리
- Gemini AI가 4가지 기준으로 분석:
  - **소송가능성** (High/Medium/Low)
  - **피해규모** (대규모/중규모/소규모/불명)
  - **집단소송** (High/Medium/Low)
  - **투자적합도** (High/Medium/Low)
- 분석 결과 + 한줄 요약 자동 저장

## Dashboard Features

- 전체/분석완료/투자적합 High/미분석 통계
- 투자적합도 기준 필터링 (High/Medium/Low)
- 기사 원문 링크 연결
- 5분 자동 새로고침
