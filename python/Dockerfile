ARG PY_BASE_IMG=3.8

FROM python:${PY_BASE_IMG}

WORKDIR /app

# RUN apk add --update --no-cache gcc python3-dev build-base libev-dev libffi-dev bash
ENV DEBIAN_FRONTEND=noninteractive
RUN sed -i 's|http://\(.*\).debian.org/debian|http://mirrors.tuna.tsinghua.edu.cn/debian|g' /etc/apt/sources.list.d/debian.sources
RUN apt-get update && apt-get install -y build-essential python3-dev libev-dev libffi-dev libgl1

COPY requirements.txt /app
RUN pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple -r requirements.txt

COPY *.py /app

ENV PYTHONUNBUFFERED 1
ENTRYPOINT ["python3"]
CMD ["server.py"]
