# STM32G tabanlı NEMA17 sürücü kartı 

> Bu proje, NEMA17 gibi step motorları alanın az olduğu yerlerde hem kompakt boyut sağlamak hemde kablo karmaşını en aza indirmek için tasarlanmıştır.

<img width="895" height="841" alt="resim" src="https://github.com/user-attachments/assets/1fb74603-1b79-4b42-99e4-5efa30e3bd3d" />


## 📋 Özellikler

* MCU: STM32G431CBT6
* Çalışma Gerilimi: 24V
* Haberleşme: CAN/CAN-FD: Kartta iki tane CAN konnektörü vardır. Bu sayede aynı karta veya aynı CAN hattı üzerindeki başka bir kartla haberleşmek için bir konnektöre giriş yapıp diğer konnektörden çıkabilirsiniz ve diğer cihaza giriş yapabilirsiniz. Dikkat: Eğer kartı CAN                   hattının son cihazı ise 60 ohmları buna uygun bir şekilde montajlayın !!!!
              I2C: Eğer motorda redüktör varsa ve kartın arkasındaki encoder kullanılmak istenmezse harici ucuz bir encoder (AS5600) girişi redüktör ucundan alınması içindir. Diğer amacı ise yine bir encoder bağlayıp redüktör boşluğu (backlash) tespiti yapılabilmesi içindir.
              USART: Debug veya direkt haberleşme sağlanabilmesi için. 
* Koruma: 26V seviyesini aşarsa sürücü koruması için TVS diyot
* Encoder: AS5147-P ----> Kartın direkt arkasında bulunur ve pahalı ve kaliteli seçilmesinin sebebi ise redüktör eklenen motorlarda milin daha hızlı dönmesinden dolayı açı verisinin kaçmasını engellemek içindir.
           AS5600   ----> Karta harici bir şekilde girilebilir. Kart üzerinde bunun için harici I2C konnektörü vardır.
* NTC: Kart üzerindeki sıcaklığı tespit etmek için kullanılabilir.
* FAN: NTC'den alınan verilere göre veya manuel soğutma için 24V fan desteği vardır.
* Sürücü: TMC2209 seçilmiştir ama TMC2208 veya pinleri uyuşan başka bir sürücüde kullanılabilir. 

## 📂 Depo İçeriği

* `/Hardware`: KiCAD şematik (`.kicad_sch`) ve PCB (`.kicad_pcb`) tasarım dosyaları.
* `/production`: Üretime hazır Gerber ve Drill dosyaları.
* `/software`: Kartın robot kol eksenlerindeki motorları kontrolü için hazırlanmış gömülü kodu.

## Tavsiyeler

* Güç girişine 50V / 1000uF seviyelerinde bir elektrolit kapasitör eklenmesi.
* Sürücülerin bozulması durumları düşünüldüğü için modül olarak yerleştirilmiştir ve modulün altı boş olduğu için burayada 50V / 220uF seviyelerinde elektrolit kapasitör eklenmesi.
* Daha kararlı bir çalışma olabilmesi için sürücü üzerine soğutucu (heatsink) yerleştirin.
* Daha soğuk bir çalışma için soğutu bloğu buck converter üzerinede yerleştirebilirsiniz.


## Diğer Görseller

<img width="808" height="816" alt="resim" src="https://github.com/user-attachments/assets/b7679888-5ed1-4ed9-85e3-b62b688bd842" />



<img width="733" height="718" alt="resim" src="https://github.com/user-attachments/assets/2970964d-a22b-488a-9b87-c5d7c9c3d9d1" />



<img width="1920" height="1080" alt="FAN" src="https://github.com/user-attachments/assets/dbee32a4-baf1-4292-b200-2eafe12caf1b" />
