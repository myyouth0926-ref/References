### 1. 통계정보
##### 1. 오브젝트 통계
##### 1-1. 테이블 통계
- 프로시저 생성    
```
begin
	dbms_stats.gather_table_stats('스키마 명', '테이블 명')
end
```
- 통계정보 조회    
```
select num_rows, blocks, avg_row_len, sample_size, last_analyzed
from all_tables
where owner = '스키마 명'
and table_name = '테이블 명';
```
##### 1-2. 인덱스 통계
##### 1-3. 컬럼 통계
##### 1-4. 히스토그램 통계
##### 2. 시스템 통계



##### 1. 선택도(Selectivity)
전체 레코드 중에서 조건절에 의해 선택되는 레코드 비율.
> **선택도 = 1 / NDV**
##### 2. NDV(Number of Distinct Values)
컬럼 값 종류 개수. 한 컬럼에 `Y`, `N` 두 값만 저장된다면, NDV = 2.    
##### 3. 카디널리티(Cardinality)
전체 레코드 중에서 조건절에 의해 선택되는 레코드 개수.
>**카디널리티 = 총 로우 수 X 선택도 = 총 로우 수 / NDV**

<span style="color: red; font-weight: bold;">비용을 계산하는 출발점은 선택도 = NDV 값을 정확히 구하는 것이 매우 중요 = 통계정보 수집주기, 샘플링 비율 등을 잘 결정해야 함</span>
