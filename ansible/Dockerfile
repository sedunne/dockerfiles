FROM python:3-slim

WORKDIR /ansible
COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

CMD [ "ansible", "--version" ]
