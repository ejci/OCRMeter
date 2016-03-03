FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install -y wget automake build-essential libtool libleptonica-dev imagemagick nodejs npm
RUN cd /tmp && wget https://github.com/tesseract-ocr/tesseract/archive/3.04.01.tar.gz && tar zxvf 3.04.01.tar.gz
RUN cd /tmp/tesseract-3.04.01 && ./autogen.sh && ./configure && make && make install && ldconfig
RUN cd /usr/local/share/tessdata && \
    wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.traineddata && \
    wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.tesseract_cube.nn && \
    wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.cube.word-freq && \
    wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.cube.size && \
    wget https://raw.githubusercontent.com/tesseract-ocr/tessdata/master/eng.cube.params && \
    wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.cube.nn && \
    wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.cube.lm && \
    wget https://raw.githubusercontent.com/tesseract-ocr/tessdata/master/eng.cube.fold && \
    wget https://raw.githubusercontent.com/tesseract-ocr/tessdata/master/eng.cube.bigrams

ADD . /app
WORKDIR /app
CMD nodejs server --path=.

EXPOSE 9090

