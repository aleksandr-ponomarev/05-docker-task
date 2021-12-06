FROM python:3.9.9 as base
COPY requirements.txt .
RUN set -xe \
		&& pip3 install -r requirements.txt
		
FROM python:3.9.9-alpine
COPY --from=base /root/.cache /root/.cache
COPY --from=base requirements.txt /flask/

WORKDIR /flask

RUN set -xe \
		&& pip3 install -r /flask/requirements.txt \
		&& rm -rf /root/.cache

COPY . /flask/

EXPOSE 5000

CMD ["gunicorn", "-c", "gunicorn.py", "app:app"]