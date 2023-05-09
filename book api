import requests
import csv

# API 요청 URL과 매개변수
url = 'https://www.googleapis.com/books/v1/volumes'
params = {
    'q': 'genre:로맨스',  # 판타지 장르 검색어
    'maxResults': 20,   # 최대 20개의 결과 반환
}

# API 요청 및 데이터 가져오기
response = requests.get(url, params=params)
data = response.json()

# CSV 파일로 저장하기
with open('로맨스.csv', mode='w', encoding='utf-8', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['제목', '작가', '출판사', '출판일', '가격', '책 정보', '썸네일 URL'])

    for book in data['items']:
        title = book['volumeInfo']['title']
        authors = book['volumeInfo'].get('authors', ['N/A'])
        publisher = book['volumeInfo'].get('publisher', 'N/A')
        published_date = book['volumeInfo'].get('publishedDate', 'N/A')
        price = book['saleInfo'].get('retailPrice', {}).get('amount', 'N/A')
        description = book['volumeInfo'].get('description', 'N/A')
        thumbnail_url = book['volumeInfo']['imageLinks'].get('thumbnail', 'N/A')

        writer.writerow([title, ', '.join(authors), publisher, published_date, price, description, thumbnail_url])
