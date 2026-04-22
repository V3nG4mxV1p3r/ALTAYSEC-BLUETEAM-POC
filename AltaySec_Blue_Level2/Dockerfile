FROM ubuntu:22.04

# Gerekli paketleri kuruyoruz
RUN apt-get update && apt-get install -y wget curl nano grep gawk && \
    wget https://github.com/yudai/gotty/releases/download/v1.0.1/gotty_linux_amd64.tar.gz && \
    tar -zxvf gotty_linux_amd64.tar.gz && \
    mv gotty /usr/local/bin/ && \
    rm gotty_linux_amd64.tar.gz

WORKDIR /home/analyst

# Dosyaları içeri aktar
COPY access.log /home/analyst/access.log

# Yeni görev talimatlarını oluştur
RUN echo "LEVEL 2: BASE64 \n\n" > gorev.txt && \
    echo "GOREV: \n1- Saldirganin sabit kalan User-Agent'ini bul. \n2- Basarili giris yapilan IP'yi tespit et. \n3- cmd parametresindeki Base64 komutu decode et. \n\nFlag: ALTAYSEC{UserAgent_IP_Komut}" >> gorev.txt

EXPOSE 80

# Terminali başlat
CMD ["gotty", "-w", "-p", "80", "bash"]