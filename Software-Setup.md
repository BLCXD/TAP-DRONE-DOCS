# Konfiguracja Oprogramowania (Software Setup)

Dokumentacja opisuje ustawienie środowiska dla całego systemu lotnego oraz naziemnego.

## 1. Dron - Kontroler Lotu (SpeedyBee F405)

### Betaflight / INAV
Dla celów misji ratowniczych i autonomii zalecane jest użycie systemu **INAV** lub **ArduPilot** (wersja dla procesorów STM32).
1. Zflashuj kontroler lotu SpeedyBee F405 systemem INAV za pomocą konfiguratora na PC.
2. Ustaw odpowiednie wyjścia na silniki EMAX 2207 i zastosuj standardowe filtry PID.
3. Włącz obsługę protokołu **MAVLink** na porcie UART, pod który podłączone jest radio Holybro SiK. Ustaw odpowiedni *baudrate* (zazwyczaj 57600).

## 2. Dron - Komputer Pokładowy AI (Jetson Orin Nano)

Głównym zadaniem układu NVIDIA Jetson jest odbieranie obrazu z kamery RunCam, przepuszczanie go przez sieć neuronową w czasie rzeczywistym i ewentualnie wysyłanie odpowiednich komend przez MAVLink.

### Środowisko
1. Na Jetsonie instalujemy system Ubuntu dostarczany z pakietem **NVIDIA JetPack**.
2. Instalujemy pakiety `OpenCV` (skompilowane ze wsparciem CUDA, aby maksymalnie wykorzystać kartę graficzną Orin Nano).
3. Wgrywamy model sieci **YOLOv8** zoptymalizowany pod TensorRT, który zajmie się wykrywaniem sylwetek ludzkich (Search & Rescue).
4. (Opcjonalnie) Skrypt w Pythonie (biblioteka `pymavlink`) może nasłuchiwać portu szeregowego łączącego Jetsona z SpeedyBee, aby wysyłać komendy korygujące lot, gdy wykryje poszkodowanego.

## 3. Aparatura (Raspberry Pi 4 GCS)



### Środowisko QGroundControl
1. Na systemie Raspberry Pi OS wgrywamy program **QGroundControl** (QGC).
2. QGC natywnie obsługuje podłączone joysticki (nasze zaprogramowane Arduino). Należy wejść w ustawienia "Virtual Joystick / Gamepad" i skonfigurować osie Throttle, Yaw, Pitch i Roll.
3. Radio SiK podłączone pod USB zostanie wykryte jako port `/dev/ttyUSB0`. W QGC dodajemy nowe połączenie telemetrii (Comm Link) wskazujące na ten port szeregowy z prędkością 57600 baud.
4. Za pomocą QGC, korzystając z MAVLink i drążków z aparatury, sterujemy dronem za pomocą komend `RC_OVERRIDE`.
