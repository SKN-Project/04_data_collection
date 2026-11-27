# 데이터 수집과 네이버 뉴스 검색 앱

Open API와 웹 스크래핑으로 데이터를 수집하고, 수집한 뉴스의 검색·저장·재조회를 Streamlit과 MySQL로 연결한 실습입니다.

## 대표 실습

- [네이버 뉴스 Open API](01_openapi.ipynb), [정적 페이지 스크래핑](04_정적웹페이지_스크래핑.ipynb), [동적 페이지 스크래핑](05_동적웹페이지_스크래핑.ipynb)에서 JSON 응답, Beautiful Soup, Selenium을 각각 사용합니다.
- [앱 진입점](streamlit_naver_news/app.py)은 API 검색과 DB 조회 화면을 나눕니다. [API 모듈](streamlit_naver_news/api/naver_news_api.py)이 응답을 뉴스 객체로 변환하고, [저장소 모듈](streamlit_naver_news/db/news_repository.py)이 저장과 재조회를 맡습니다.
- [테이블 정의](naver_news.sql)는 링크에 유일성 제약을 두어 동일 링크의 중복 저장을 방지합니다.

## 실행

MySQL의 실습용 스키마에 [naver_news.sql](naver_news.sql)을 적용합니다. 앱의 `.env`에는 [설정 코드](streamlit_naver_news/config/settings.py)에 나온 `NAVER_CLIENT_ID`, `NAVER_CLIENT_SECRET`과 DB 접속 정보를 설정합니다.

```bash
cd streamlit_naver_news
python -m pip install streamlit requests pandas python-dotenv mysql-connector-python
python -m streamlit run app.py
```
