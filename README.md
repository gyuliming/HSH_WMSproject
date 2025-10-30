# 📦 WMS Project

창고 관리(Warehouse Management System)를 위한 프로젝트입니다.
본 시스템은 가구 재고 관리와 입출고 현황 파악을 목적으로 하며, Java + JDBC + MySQL 기반으로 구현되었습니다.
MVC 패턴을 적용해 유지보수성과 확장성을 고려했습니다.

---

## 🛠️ 기술 스택

- Language : Java (JDK 17)
- Database : MySQL 8.0.22
- Database Access : JDBC
- Tooling : IntelliJ IDEA, GitHub, Workbench, Railway

---

## 📂 프로젝트 구조

```
src/
 ┣ controller/   # 사용자 요청 처리
 ┣ service/      # 비즈니스 로직
 ┣ serviceImpl/    # Service 구현체 (비즈니스 로직 실제 처리)
 ┣ dao/          # 데이터 접근 인터페이스
 ┣ daoImpl/      # DAO 구현체 (JDBC 활용)
 ┣ domain/          # Vo, Dto
 ┣ Session/       # 사용자 로그인 정보 저장
 ┗ view/         # CLI 기반 UI
```

---

## 🔀 Git Flow 전략

우리 팀(4명)의 협업을 위해 Git Flow 전략 및 커밋 컨벤션을 사용했습니다.
**feature → develop → main** 순서로 merge 진행

- main: 실제 서비스 배포용 안정 브랜치
- develop: 기능 통합 브랜치
- feature/: 새로운 기능 개발 브랜치
    - feature/inbound-outbound : 입출고 관리
    - feature/inventory : 재고 관리
    - feature/member-board : 회원/로그인 관리
    - feature/warehouse : 창고 관리

---

## ✨ 주요 기능

- 입출고 관리 : 상품 입고/출고 내역 기록 및 추적
- 재고 관리 : 창고별 재고 조회 및 실사 관리
- 회원/로그인 관리 : 사용자 등록, 로그인, 권한별 기능 접근
- 창고 관리 : 기능별 창고 조회 및 창고/섹션 등록·수정

---

## 내가 한 일

### 🧾 재고 관리

> 사용자가 로그인을 하면 각 사용자의 역할(Role) 정보가 세션에 저장이 되어서 정보에 따라 접근할 수 있는 재고 관리 범위와 기능이 제한되어 있다.
> 회원(매장 관리자)는 매장 창고에 해당하는 재고만 관리할 수 있고, 창고 관리자는 해당 창고의 재고를 보다 넓게 관리할 수 있고, 총 관리자는 모든 창고의 재고를 관리할 수 있다.


**회원(매장 관리자)**

1. `displayAllInventory()` 메서드로 매장 창고에 있는 전체 재고를 조회할 수 있다.
2. `displayProductDetail()` 메서드로 매장 창고에 있는 상품의 상세 조회를 할 수 있다.

**관리자(창고 관리자)**

1. `displayAllInventory()` 메서드로 관리하는 창고의 전체 재고를 조회할 수 있다.
2. `displayTopCategoryInventory()` 메서드로 관리하는 창고에 있는 재고들을 대분류 카테고리별로 조회할 수 있다.
3. `displayTopCategoryInventory()` 메서드로 관리하는 창고에 있는 재고들을 소분류 카테고리별로 조회할 수 있다.
4. `displayProductDetail()` 메서드로 관리하는 창고에 있는 상품의 상세 정보를 조회할 수 있다.
5. `displayWarehouseInventory()` 메서드로 관리하는 창고의 현황을 조회할 수 있다.
6. `displayInventoryAuditLog()` 메서드로 재고실사 기록을 조회할 수 있다.

**관리자(총 관리자)**

1. `displayAllInventory()` 메서드로 모든 창고의 전체 재고를 조회할 수 있다.
2. `displayTopCategoryInventory()` 메서드로 모든 창고에 있는 재고들을 대분류 카테고리별로 조회할 수 있다.
3. `displayTopCategoryInventory()` 메서드로 모든 창고에 있는 재고들을 소분류 카테고리별로 조회할 수 있다.
4. `displayProductDetail()` 메서드로 모든 창고에 있는 상품의 상세 정보를 조회할 수 있다.
5. `displayWarehouseInventory()` 메서드로 모든 창고의 현황을 조회할 수 있다.
6. `displayInventoryAuditLog()` 메서드로 재고실사 기록을 조회할 수 있다. 

---

## 🔗 관련 링크

- 초기 설계 : https://www.notion.so/WMS-1-29cd50c267e080e68ecec6d95a1cad63?source=copy_link
- ERD : https://www.erdcloud.com/d/MENawiffwtcqhyHir

---

## ⚙️ 개선 목표

- 예외 처리
   - MVC 패턴 설계에 집중을 하다보니, 예외 처리가 미비해서 프로그램이 비정상적으로 종료될 가능성이 있기에, 이 부분을 개선할 계획입니다.
     
-  기능 구현 
   - 초기에 요구 사항과 기능 명세서 부분을 제작할 때, 시간 분배를 잘 못해서 초기에 정해놨던 기능을 전부 구현하지 못했습니다. 이 부분들을 추가할 계획입니다.
  
- 중복 코드
   - 조회를 하는 부분에서 반복되는 로직이 다수 존재합니다. 쿼리문이나 서비스 로직을 재사용 가능한 메서드로 정리할 계획입니다.

---
 
## 💭 프로젝트 후기 및 회고록

https://velog.io/@gyuliming/SSG-1%EC%B0%A8-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8


