# 인공지능사관학교 전통주 추천 팀 프로젝트

## 프로젝트 개요

- 기간: 2023.07 ~ 2023.08
- 목적: 전통주 정보 제공과 사용자 취향 기반 개인화 추천 기능을 결합한 Flask 웹 서비스 구현
- 담당: 전통주·양조장 데이터 수집, Selenium 기반 웹 크롤링, 설문 데이터 전처리·시각화, 추천 로직 설계 참여

## 데이터와 추천 방식

- 한국농수산식품유통공사 전통주·양조장 데이터 활용
- 술담화 웹 페이지에서 이미지·설명·태그 등 서비스용 정보 수집
- Google Form과 대면 설문으로 취향 데이터 수집 및 전처리
- 입력 특성: 성별, 연령대, 주종, 단맛, 신맛, 바디감, 도수, 가격

## 실험과 최종 구현 구분

### KNN 분류 실험

- 설문 취향 데이터를 정규화한 뒤 학습·평가 데이터를 8:2로 분리
- `KNeighborsClassifier(n_neighbors=3)`로 Accuracy·Precision·Recall·F1-score 평가
- 당시 프로젝트 결과 기록 기준 Accuracy 85% 확인
- 이 수치는 최종 웹 서비스 전체의 추천 정확도가 아니라 KNN 분류 실험 결과임

### 최종 Flask 추천 서비스

- 성별·연령대·주종으로 설문 데이터를 우선 필터링
- 설문 응답과 사용자 입력 간 코사인 유사도로 사용자 기반 추천 계산
- 전통주 맛·도수·가격 등 특성과 사용자 입력 간 코사인 유사도로 아이템 기반 추천 계산
- 사용자 기반 추천 2개와 아이템 기반 추천 2개를 결합해 최대 4개 결과 반환

## 수치 표기 기준

- 사용 가능: `KNN 분류 실험 당시 기록 기준 정확도 85%`
- 사용하지 않음: `최종 추천 시스템 정확도 85%`
- 근거가 확인되지 않은 사용자 만족도 92%, 설문 응답자 430명, 유사도 최대 99.9%는 공식 성과 수치로 사용하지 않음

## 원본 연결

- Google Drive 프로젝트 폴더: https://drive.google.com/drive/folders/18amG4fD1N0B3rDplaahvGkyDQx_QreGl
- Google Drive 자료 인덱스: https://docs.google.com/document/d/1pjnMLxNGu-WYWE-R91j1bqAXBFtQjhe6LaqFPZwJWXc/edit
- Notion 팀 프로젝트: https://app.notion.com/p/1d63ec04c6ec8147aa2cf4afdd73e61b
- Notion 기획발표 대본: https://app.notion.com/p/1d63ec04c6ec81a0aa01c399f381ed6f

## 주요 코드

- Flask 애플리케이션: `korean_drink/app.py`
- 최종 추천 로직: `korean_drink/service/recommand.py`
- KNN 분류 실험: `머신러닝/KNN.py`

## 관리 기준

- 실행 코드와 데이터는 GitHub 원본을 우선 확인
- 기획·실험 기록은 Notion에서 확인
- 발표자료와 취업 문서는 본 문서의 실험·최종 구현 구분에 맞춰 동기화
- Drive는 프로젝트 자료와 최신 취업 문서를 찾기 위한 관리 위치