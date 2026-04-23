# AltaySec Blue Team Lab - Level 3 (Log Analysis)
FROM ubuntu:22.04

# Analizcinin ihtiyaç duyacağı temel araçları kuruyoruz
RUN apt-get update && apt-get install -y \
    nano \
    vim \
    grep \
    gawk \
    coreutils \
    jq \
    && rm -rf /var/lib/apt/lists/*

# Öğrenci için 'analyst' adında yetkisiz bir kullanıcı oluşturuyoruz
RUN useradd -m -s /bin/bash analyst

# Log dosyalarını ve görev metnini öğrencinin ev dizinine kopyalıyoruz
WORKDIR /home/analyst
COPY access.log .
COPY system_audit.log .
COPY gorev.txt .

# Dosya izinlerini ayarlıyoruz (Sadece okuyabilsinler, silemesinler)
RUN chown root:root access.log system_audit.log gorev.txt
RUN chmod 444 access.log system_audit.log gorev.txt

# Öğrenci konteynere bağlandığında bu kullanıcı ile başlasın
USER analyst

# Konteynerin kapanmaması için sonsuz bir döngüde çalıştırıyoruz
CMD ["tail", "-f", "/dev/null"]