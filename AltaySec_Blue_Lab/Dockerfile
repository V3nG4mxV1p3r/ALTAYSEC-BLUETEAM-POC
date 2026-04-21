FROM ubuntu:22.04

RUN apt-get update && apt-get install -y wget curl nano grep gawk && \
    wget https://github.com/yudai/gotty/releases/download/v1.0.1/gotty_linux_amd64.tar.gz && \
    tar -zxvf gotty_linux_amd64.tar.gz && \
    mv gotty /usr/local/bin/ && \
    rm gotty_linux_amd64.tar.gz

WORKDIR /home/analyst

COPY access.log /home/analyst/access.log
RUN echo "GOREV: access.log dosyasini incele. Saldirgan IP'sini, kullanilan parametreyi (page=...) ve okunan dosyayi bul. Flag formati: ALTAYSEC{IP_PARAMETRE_DOSYA}" > gorev.txt

EXPOSE 80

CMD ["gotty", "-w", "-p", "80", "bash"]