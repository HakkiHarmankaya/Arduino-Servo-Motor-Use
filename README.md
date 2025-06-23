# 🎮 Arduino #12: Joystick ile Servo Motor Kontrolü

Bu projede, bir **joystick modülü** kullanarak bir **servo motorun açısını kontrol etmeyi** öğreneceğiz.  
Joystick hareket ettikçe, servo motor belirlenen eksende dönecektir.

🔗 [Web Siteme Bakmak İçin Tıkla](https://www.hakkiharmankaya.com/)  


---

## 🧰 Gerekli Malzemeler

- 1 adet **joystick modülü**
- 1 adet **servo motor**
- 1 adet **Arduino**
- 1 adet **breadboard**
- **Jumper kabloları**

---

## ⚙️ Adım Adım Devre Kurulumu

### 🔹 Adım 1: Devreyi Kurun

- **Joystick modülü**:
  - **VCC** → **5V**
  - **GND** → **GND**
  - **VRx** → **A0** (X ekseni)
  - **VRy** → **A1** (Y ekseni – bu örnekte kullanılmayacak)

- **Servo motor**:
  - **Sinyal (sarı)** → **D3**
  - **VCC (kırmızı)** → **5V**
  - **GND (siyah/kahverengi)** → **GND**

---

## 🔹 Adım 2: Arduino Kodunu Yazın ve Yükleyin

```cpp
#include <Servo.h>

Servo motor;
int deger;
int derece;

void setup() {
  motor.attach(3); // Servo motoru 3. pine bağla
}

void loop() {
  deger = analogRead(A0);               // Joystick X eksenini oku
  derece = map(deger, 0, 1023, 0, 180); // 0-1023 → 0-180 derece
  motor.write(derece);                  // Servo motoru belirtilen açıya döndür
}
