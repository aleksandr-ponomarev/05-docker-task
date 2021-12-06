FROM python:3.9.9-slim

WORKDIR /app
COPY requirements.txt .

RUN set -xe \
		&& pip install -r /flask/requirements.txt \
		&& rm -rf /root/.cache

COPY . /app/

RUN pwd && ls -lah

EXPOSE 5000

CMD ["gunicorn", "-c", "gunicorn.py", "app:app"]