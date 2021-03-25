---
layout: single
title: 금융 IT시스템의 구조
categories:
  - 금융IT
tags:
  - 금융IT
---

## 금융기관의 종류
1. 은행
2. 금융투자사(증권사, 자산운용 등)
3. 카드사
4. 보험사
5. 금융 보조 기관
 - 금융감독원, 한국거래소, 금융결제원, 예금보험공사 등

## 금융 IT시스템의 구조
###1. 계정계(Core Banking)
- 계좌 개설, 입출금, 이체, 외환 등 핵심업무
- 가장 핵심적인 시스템으로 매우 보수적으로 운영됨(삼중백업 등)

###2. 정보계
- 계정계 데이터를 기반으로 거래 데이터에 대한 *기록* 및 *기록의 통계*를 관리
- CRM, 신용 평가, 리스크 관리, 수익관리, 마케팅 등(돈과 관련X)
- 최근 고객 중심 서비스가 중요해지면서 고객 접점에서 즉각적인 마케팅의 개인화가 가능하도록 빅데이터 분석 기술이 가장 많이 활용되고 있음 - Data Warehouse(DW) 업무라고 별도로 분리해서 부르기도 함
- T-Solution에는 정보계가 따로 없고 계정계+정보계 = BOS 시스템

###3. 대외계
- 외부 기관과 연계되는 업무를 처리하기 위한 연결 시스템
- 인터넷 뱅킹, 주식 주문, 타행이체, 카드결제 등
- 거래내역 검증, 네트워크 오류 관리 등 매우 복잡한 구조로 운영됨
- 대용량 처리보다는 정확성과 안정성 중심(C를 사용하는 이유)

###4. 채널계
- 대외계 시스템 및 여러 비대면 채널을 관리하는 시스템
- End User에 따른 다양한 접속 채널에서 발생하는 데이터를 관리
- 모바일뱅킹, HTS, WTS, MTS 등

###5. 운영계
- IT 시스템의 안정적인 운영을 위한 통합 관제, 네트워크 모니터링, 유지보수 등을 담당

## 금융권에서 Java를 많이 사용하는 이유
- C/C++은 OS에서 직접 컴파일되는 시스템 언어로, 컴파일 시 CPU사용률이 100% 사용할 수 있다는 장점이 있다.
- 하지만 C는 OS가 달라지면 재컴파일 해야하기 때문에, OS마다 시스템함수가 다르면 꽤 많은 부분을 수정해야하는 번거로움이 있다. 즉 *이식성*이 떨어진다.
- 서버가 100대가 넘어가는 대규모의 금융 시스템에서는 관리 상태나 노후 상태가 모두 다르기 때문에, 하드웨어 특성에 관계 없이 서버가 운영될 필요가 있다. 
- 그렇기 때문에 JVM(Java Virtual Machine) 위에서 돌아가 운영체제 종류에 영향을 받지 않는 *이식성*이 높은 언어인 Java를 많이 사용한다.
- 돈과 직접적인 관련이 있는 정보계나, 처리속도가 중요한 증권 서버 시스템에서는 C를 많이 사용한다.