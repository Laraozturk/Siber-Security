# ***CRONTAB NEDİR VE NASIL KULLANILIR?***
# **1.Crontab Nedir?**
Belirli bir zamanda tekrarlanacak olan görevlerin bir komut dosyasını oluşturan bir Unix komutudur.
# **2.Nasıl Kullanılır?**
┌───────────── dakika (0 – 59)
│ ┌───────────── saat (0 – 23)
│ │ ┌───────────── takvim günü (1 – 31)
│ │ │ ┌───────────── ay (1 – 12)
│ │ │ │ ┌───────────── gün (0 – 6) (0=Pazar, 1=Pazartesi … 6=Cumartesi
│ │ │ │ │                                            ve ayrıca sadece Pazar günü için 7=Pazar)
│ │ │ │ │
│ │ │ │ │
*  *  *  * *  çalıştırılmak istenen komut dizini
# **Crontab Kullanımı Örneği**
Her saat başı ornek2.sh scriptini çalıştıracak kod aşağıdaki gibidir.
'''
0 * * * * /home/kali/yedek/ornek2.sh
'''
