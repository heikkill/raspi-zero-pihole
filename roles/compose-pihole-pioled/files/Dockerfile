FROM insightful/alpine-python:3.6-arm32v6

USER root
RUN apk add gcc python3-dev linux-headers freetype freetype-dev
RUN pip3 install adafruit-circuitpython-ssd1306 requests RPi.GPIO Pillow
RUN mkdir -p /opt/pioled/silkscreen \
    && cd /opt/pioled/silkscreen \
    && wget http://kottke.org/plus/type/silkscreen/download/silkscreen.zip \
    && unzip silkscreen.zip \
    && mv slkscr.ttf ../ \
    && cd .. \
    && rm -rf silkscreen
COPY ./stats.py /opt/pioled/

CMD [ "python", "/opt/pioled/stats.py", "dummy" ]