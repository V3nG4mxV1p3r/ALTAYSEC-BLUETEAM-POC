FROM ubuntu:22.04

RUN apt-get update && apt-get install -y wget curl nano grep gawk && \
    wget https://github.com/yudai/gotty/releases/download/v1.0.1/gotty_linux_amd64.tar.gz && \
    tar -zxvf gotty_linux_amd64.tar.gz && \
    mv gotty /usr/local/bin/ && \
    rm gotty_linux_amd64.tar.gz

WORKDIR /home/analyst

# Dosyaları içeri kopyala
COPY access.log /home/analyst/access.log
COPY submit.sh /home/analyst/submit.sh

# Görev dosyasını oluştur, scripti çalıştırılabilir yap ve Windows satır sonu (\r) hatasını düzelt
RUN echo "LEVEL 1: RECON & BRUTE FORCE \n\nGOREV: access.log dosyasini incele ve bulgularini not et. \nHazir oldugunda terminale './submit.sh' yazarak cevaplarini sisteme gir ve bayragini (Flag) al!" > gorev.txt && \
    chmod +x /home/analyst/submit.sh && \
    sed -i 's/\r$//' /home/analyst/submit.sh

EXPOSE 80

CMD ["gotty", "-w", "-p", "80", "bash"]