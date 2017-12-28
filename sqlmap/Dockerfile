FROM python:2.7

ENV VERSION 1.0.11

RUN apt-get update && apt-get install -y \
		git --no-install-recommends

RUN mkdir /app

WORKDIR /app

RUN git clone https://github.com/sqlmapproject/sqlmap.git . \
&& git checkout tags/${VERSION}

CMD ["./sqlmapapi.py", "-s", "-H", "0.0.0.0", "-p", "7775"]
