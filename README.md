# ***SHELL SCRİPT SERVİS OLARAK AYARLAMA***

## **1. Shell Script Dosyası Oluşturma**

Her saat başı yedek alan Shell script oluşturduk. Oluşturduğumuz script yedekleme alınan saati dosyanın ismi yapar. 

```
#!/bin/bash
# Yedek almak için fonksiyon
backup_files(){
    local source_dir=$1
    local backup_dir=$2
    local current_time=$(date "+%Y%m%d%H")
    local backup_filename="${current_time}_backup.tar.gz"
 
    tar -czf "${backup_dir}/${backup_filename}" -C "${source_dir}" .
    echo "yedekleme tamamlandı: ${backup_dir}/${backup_filename}"
}
#saat başı yedeklemeyi kontrol eder
while true; do 
    #şuanki dakika bilgisini al
    current_minute=$(date +"%M")
    # Eğer saat başı ise yedekleme işlemini gerçekleştir
    if [[ "$current_minute" == "00" ]]; then 
    # Yedekleme işlemini gerçekleştir
    source_directory="/home/kali/odevy" #scriptlerin olduğu dizin
    backup_directory="/home/kali/task" # Yedeklerin kaydedileceği dizin
    backup_files "$source_directory" "$backup_directory"
    fi
done
```

## **2. Oluşturduğumuz Scriptte Bulunan Gereksiz Kodları Çıkarma (While Döngüsü)**

```
#!/bin/bash
# Yedek almak için fonksiyon
backup_files(){
    local source_dir=$1
    local backup_dir=$2
    local current_time=$(date "+%Y%m%d%H")
    local backup_filename="${current_time}_backup.tar.gz"
 
    tar -czf "${backup_dir}/${backup_filename}" -C "${source_dir}" .
    echo "yedekleme tamamlandı: ${backup_dir}/${backup_filename}"
}
#saat başı yedeklemeyi kontrol eder
    #şuanki dakika bilgisini al
    current_minute=$(date +"%M")
    # Eğer saat başı ise yedekleme işlemini gerçekleştir
    if [[ "$current_minute" == "00" ]]; then 
    # Yedekleme işlemini gerçekleştir
    source_directory="/home/kali/odevy" #scriptlerin olduğu dizin
    backup_directory="/home/kali/task" # Yedeklerin kaydedileceği dizin
    backup_files "$source_directory" "$backup_directory"
    fi
```

## **3. Servis Dosyası Oluşturma**

```
sudo nano /lib/systemd/system/yedekleme3.service 
```

## **4. Servis Dosyasının İçine Yazılan Kodlar**

```
[Unit]
Description=My Shell Script

[Service]
ExecStart=/home/kali/odevy/yedekleme.sh

[Install]
WantedBy=multi-user.target
```

## **5. Systemctl Servis Dosyalarını Yapılandırma**

```
sudo systemctl daemon-reload 
```

## **6.Oluşturduğumuz Servisin Otomatik Olarak Çalışması**

```
sudo systemctl enable yedekleme3.service 
```

## **7.Servisin Başlatılması**

```
sudo systemctl start yedekleme3.service 
```

## **8.Servisin Durumunu ve Çalışma Bilgilerini Görüntüleme**

```
sudo systemctl status yedekleme3.service 
```
