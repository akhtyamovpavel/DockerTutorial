FROM python:3.4-alpine

ARG gitcommithash

ADD . /code
WORKDIR /code
RUN pip install -r requirements.txt

RUN apk update && apk upgrade && \
    apk add --no-cache bash git

RUN git clone https://github.com/vishnubob/wait-for-it.git
RUN cd wait-for-it && git reset ${gitcommithash} --hard
RUN cp wait-for-it/wait-for-it.sh ./
CMD ["python", "app.py"]
