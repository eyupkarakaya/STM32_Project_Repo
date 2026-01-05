# 1. LED Blink (Yanıp Sönen Işık)

Bu uygulama, geliştirme ortamının (IDE) doğru kurulduğunu ve işlemcinin çalıştığını doğrulayan temel projesidir. **PE1** pinine bağlı olan **State LED**'ini yakıp söndürür.

---

## 🚀 Adım 1: Yeni Proje Oluşturma Rehberi

Geliştirme Kiti ile sıfırdan proje oluşturmak için aşağıdaki standart adımları takip edin:

### 1. Proje Sihirbazını Başlatma
1.  **STM32CubeIDE** programını açın.
2.  Sol üst menüden **File > New > STM32 Project** seçeneğine tıklayın.

<p align="center"><img src="assets/new_project.png" width="500"></p>

<br>


### 2. İşlemci Seçimi (Target Selection)
Açılan pencerede:
* **Part Number Search** kutusuna işlemcimizin modelini yazın: `STM32F103VET6`
* Sağ alttaki listeden işlemciyi seçin ve **Next** butonuna basın.

<p align="center"><img src="assets/target.png" width="500"></p>


<br>

### 3. Proje Yapılandırması
* **Project Name:** `1_Led_Blink`
* **Targeted Language:** `C`
* **Targeted Binary Type:** `Executable`
* **Finish** butonuna basın.

> **Önemli Not:** "Initialize all peripherals with their default Mode?" uyarısı gelirse **No (Hayır)** diyerek temiz bir başlangıç yapın.

<p align="center"><img src="assets/project_structure.png" width="350"></p>

<br>
<br>

## ⚙️ Adım 2: Bu Proje İçin Özel Ayarlar (CubeMX)

Projenizi oluşturduktan sonra açılan **.ioc** arayüzünde şu ayarları yapın:

1.  **Debug Ayarı:** Sol menüden **System Core > SYS** kategorisine tıklayın ve **Debug** seçeneğini `Serial Wire` yapın.

<p align="center"><img src="assets/debug.png" width="700"></p>


2.  **Pin Seçimi:** Sağ taraftaki işlemci görselinden **PE1** pinini bulun.

<p align="center"><img src="assets/pin.png" width="300"></p>

<br>

3.  **Pin Modu:** Pinin üzerine sol tıklayın ve **GPIO_Output** seçeneğini işaretleyin.
<p align="center"><img src="assets/gpio.png" width="300"></p>

<br>
<br>

**4. Detaylı Pin Konfigürasyonu:**
Sol menüden **System Core > GPIO** sekmesine gelin, listeden **PE1** pinini seçin ve aşağıdaki ayarları yapın:

| Ayar (Setting) | Seçilecek Değer |
| :--- | :--- |
| **GPIO Output Level** | `Low` |
| **GPIO Mode** | `Output Push Pull` |
| **GPIO Pull-up/Pull-down** | `No pull-up and no pull-down` |
| **Maximum Output Speed** | `Low` |
| **User Label** | `State_LED` |

<br>

<p align="center"><img src="assets/pin_config.png" width="500"></p>


*Ayarlar bittikten sonra üst menüden **Project > Generate Code** diyerek kodları oluşturun.*

<p align="center"><img src="assets/genetation.png" width="500"></p>

---

## 💻 Adım 3: Yazılım (main.c)

Kodlar oluşturulduktan sonra `Core/Src/main.c` dosyasını açın.

⚠️ **ÖNEMLİ UYARI:** Kodlarınızın CubeMX güncellemesinde silinmemesi için **mutlaka** `USER CODE BEGIN 3` ile `USER CODE END 3` arasına yazmalısınız.

`while(1)` döngüsünün içini aşağıdaki gibi düzenleyin:

```c
  /* Infinite loop */
  while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */

    HAL_GPIO_TogglePin(GPIOE, GPIO_PIN_1); // State_LED durumunu değiştir 
    HAL_Delay(500); // 500ms (Yarım saniye) bekle 

    /* USER CODE END 3 */
  }
```
<br>

## 📺 Sonuç (Demo)

Kod karta yüklendikten sonra **PE1** pinine bağlı LED'in çalışma durumu aşağıdaki gibidir:

<br>
<p align="center"><img src="assets/led_blink.gif" width="500"></p>




