# Python이 포함된 가벼운 베이스 이미지 사용
FROM python:3.9-slim  # Python 3.9와 함께 가벼운 Linux 환경 제공

# 작업 디렉토리 설정
WORKDIR /app

# 시스템 패키지 설치 및 의존성 파일 복사
RUN apt-get update && apt-get install -y \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

# requirements.txt 복사 및 패키지 설치
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

# 애플리케이션 파일 복사
COPY . /app

# uWSGI 설정을 사용하여 애플리케이션 실행
CMD ["uwsgi", "--ini", "uwsgi.ini"]
