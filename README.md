# ELK 스택과 Google Analytics API 를 활용해 통계성 데이터 제공하는 API 구현하기

# 1. 요구조건 분석

## 1.1. 서비스 개요

SNS 와 같이 많은 사람들이 컨텐츠를 즐기며 서로 상호작용 하는 커뮤니티형 서비스라고 생각해보자. <br />
(예시) 유튜브, 페이스북, 인스타그램 <br />

여기에는 크게 세 종류 이상의 도메인이 있다. <br />
(1) 컨텐츠 - content <br />
(2) 컨텐츠를 업로드하는 사용자 - uploader <br />
(3) 컨텐츠를 즐기느 사용자 - viewer or visitor <br />

### 1.2. Analytics API 요구조건

### 1.2.1. Page 1 - 사용자 관련 통계 정보

사용자 관련해서 다음과 같은 요구사항이 있다고 가정해보자. <br />

![page-01](./images/page-01.png)

(1) 통계 정보를 확인하려는 기간을 설정할 수 있다. <br />

-> 시작 시점 <br />
-> 종료 시점 <br />
-> 조회 범위는 최대 1년으로 한정 <br />
-> 데이터는 사용자가 존재하는 timezone 기준으로 보여줘야 한다. <br />

(2) 사용자 방문에 대한 통계 정보를 숫자로 확인하는 경우 <br />

다음과 같은 정보가 필요하다. <br />

-> 총 방문자 수 (total) <br />
-> 현재 기간 내 총 방문자 수 (current total) <br />
-> 이전 기간 내 총 방문자 수 (previous total) <br />
-> 방문자 수 증감률 (change rate) <br />

(3) 사용자 방문에 대한 통계 추이를 차트(그래프)로 확인하는 경우 <br />

다음과 같은 정보가 필요하다. <br />

-> 단위시간 별 방문자 수 <br />

(4) 사용자 관련해서는 다음과 같은 메트릭이 필요하다 <br />

기본적인 사용자 관련 메트릭은 다음과 같은 항목이 있다. <br />

-> 활성 사용자 수 (active user) <br />
-> 지역, 성별, 연령에 따른 사용자 수 <br />
-> 신규, 휴면, 탈퇴 사용자 수 <br />
-> 체험판 / 무료 / 구독 사용자 수 <br />

복잡한 사용자 관련 메트릭은 다음과 같은 항목이 있다. <br />

-> 중복없는 사용자 수 (unique user) <br />
-> 첫 페이지 이탈률 (bounce rate) <br />
-> 재방문율 (retention) <br />
-> 평균 방문 페이지 수 (average page view) <br />
-> 평균 페이지에 머무른 시간 (average page duration) <br />

### 1.2.2. Page 2 - 컨텐츠 관련 통계 정보

컨텐츠 관련홰서 다음과 같은 요구사항이 있다고 가정해보자. <br />

![page-02](./images/page-02.png)

(1) 통계 정보를 확인하려는 기간을 설정할 수 있다. <br />

-> 시작 시점 <br />
-> 종료 시점 <br />
-> 조회 범위는 최대 1년으로 한정 <br />
-> 데이터는 사용자가 존재하는 timezone 기준으로 보여줘야 한다. <br />

(2) 컨텐츠 조회수 통계 정보를 숫자로 확인하는 경우 <br />

-> 총 조회수 (total) <br />
-> 현재 기간 내 총 조회수 (current total) <br />
-> 이전 기간 내 총 조회수 (previous total) <br />
-> 조회수 증감률 (change rate) <br />

(3) 컨텐츠 조회수 통계 추이를 차트(그래프)로 확인하는 경우 <br />

-> 단위시간 별 컨텐츠 조회수 <br />

(4) 컨텐츠 관련해서 다음과 같은 메트릭이 필요하다. <br />

기본적인 컨텐츠 관련 메트릭은 다음과 같은 항목이 있다. <br />

-> 업로드 수 <br />
-> 조회수 <br />
-> 좋아요 수 <br />
-> 공유 횟수 <br />
-> 평균 시청 시간 <br />

컨텐츠 관련 메트릭은 다음 두 가지 항목에 대해서 수집해야 한다. <br />

-> 컨텐츠 마다의 통계 정보 <br />
-> 카테고리 별 통계 정보 <br />

# 2. 기술 분석

## 2.1. GA(Google Analytics) 와 ELK(Logstash, Elasticsearch, Kibana) 를 선택한 이유

처음에는 과거부터 데이터 분석 플랫폼으로 유명한 Hadoop, Spark 를 고려하기도 했지만

## 2.2. ELK(Logstash, Elasticsearch, Kibana) 스택

### 2.2.1. Logstash 와 Beats

Logstash 는 <br />

... <br />

Beats 는 <br />

... <br />

### 2.2.2. Elasticsearch

Elasticsearch 는 <br />

... <br />

### 2.2.3. Kibana

Kibana 는 <br />

... <br />

### 2.3. GA (Google Analytics) API

Google Analytics 는 <br />

... <br />

GA4(Google Analytics 4) 는 <br />

... <br />

# 3. 구현 과정에서 마주친 어려움

## 3.1. 셋업 과정

docker-elk 리포지토리 사용하는 방법 <br />

## 3.2. Logstash 에 로그데이터를 저장하는 형태 결정

## 3.3. Google Analytics 쿼리 횟수 제한

## 3.4. Elasticsearch 쿼리에 대한 생소함

## 3.5. 사용자 지정 시간 범위가 커지면서 예상되는 서버쪽 부하 증가

ELK 에 적재한 데이터를 시간(hour) 단위로, 일(date) 단위로 데이터베이스(MongoDB)에 마이그레이션 해두기 <br />

## 3.6. 시간단위(1 hour), 일단위(1 day)로 데이터를 적재해두는 데이터베이스 스키마 설계

만능 스키마는 없다. <br />

## 3.7. 다중 타임존 지원 요구사항

Date 또는 Timestamp 타입의 컬럼은 쿼리 결과에 timezone 적용된 결과값으로 받아오기 <br />

mongodb 에서는 <br />

```mongodb
{
    $project: {
        formattedDate: {
            $dateToString: {
                format: '%Y-%mm-%dd %HH-%MM-%SS',
                date: '$timestamp',
                timezone: 'America/New_York'
            }
        }
    }
}
```

'America/New_York': -05:00 <br />

<br />
<br />
<br />

mysql 에서는 <br />

```sql
SELECT DATE_FORMAT(CONVERT_TZ(timestamp, '+00:00', '+09:00'), '%Y-%mm-%dd %HH:%ii:%ss');
```

Asia/Seoul: +09:00 <br />

<br />
<br />
<br />

postgresql 에서는 <br />

```sql
SELECT TO_CHAR(
    DATE_TRUNC(
        'day',
        TIMESTAMP WITH TIME ZONE '2023-07-11 13:53:05+00'
    ) AT TIME ZONE 'Europe/Moscow',
    'YYYY-MM-DD HH24:MI:SS'
);
```

'Europe/Moscow': +03:00 <br />







