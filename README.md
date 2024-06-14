# MarketDB

MarketDB는 MariaDB를 사용하여 주식 시장 데이터를 관리하고 조회하는 클래스입니다. 이 클래스는 종목 코드 정보를 데이터베이스에서 읽어와 딕셔너리에 저장하고,
특정 종목의 일별 시세를 조회할 수 있는 기능을 제공합니다.

## 설치 및 환경 설정

### 필수 라이브러리

이 프로젝트를 실행하기 위해서는 다음의 Python 라이브러리가 필요합니다:

- pandas
- pymysql
- sqlalchemy

다음 명령어를 사용하여 필요한 라이브러리를 설치할 수 있습니다:

```sh
pip install pandas pymysql sqlalchemy

데이터베이스 설정
MariaDB 또는 MySQL 데이터베이스를 설정하고, 다음 정보를 업데이트해야 합니다:

server: 데이터베이스 서버 주소 (예: 'localhost')
database: 데이터베이스 이름 (예: 'INVESTAR')
username: 데이터베이스 사용자 이름 (예: 'root')
password: 데이터베이스 비밀번호 (예: 'password')


#사용법
import pandas as pd
from marketdb import MarketDB

# MarketDB 인스턴스 생성
mdb = MarketDB()

# 특정 종목의 일별 시세 조회
df = mdb.get_daily_price('005930', '2023-01-01', '2023-12-31')
print(df)


클래스 설명
__init__(self)
생성자 메서드로, 데이터베이스 연결을 설정하고 종목 코드를 딕셔너리에 저장합니다.

__del__(self)
소멸자 메서드로, 데이터베이스 연결을 해제합니다.

get_comp_info(self)
company_info 테이블에서 데이터를 읽어와 self.codes 딕셔너리에 종목 코드를 저장합니다.

get_daily_price(self, code, start_date=None, end_date=None)
특정 종목의 일별 시세를 조회하여 데이터프레임 형태로 반환합니다. 종목 코드는 KRX 종목 코드('005930') 또는 상장 기업명('삼성전자')으로 입력할 수 있습니다.
시작일과 종료일을 입력하지 않으면 기본적으로 1년 전부터 오늘까지의 데이터를 조회합니다.
