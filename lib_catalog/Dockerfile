FROM python:3.9.9 as build
COPY requirements.txt .
RUN set -xe \
		&& pip install -r requirements.txt
		
FROM python:3.9.9-alpine
COPY --from=base /root/.cache /root/.cache
COPY --from=base requirements.txt /flask/

WORKDIR /flask

RUN set -xe \
		&& pip install -r /flask/requirements.txt \
		&& rm -rf /root/.cache

EXPOSE 5000

CMD ["gunicorn", "-c", "gunicorn.py", "app:app"]