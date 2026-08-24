# Budowa Autorskiego Pilota z Raspberry Pi (GCS)

Największą innowacją w projekcie jest odrzucenie klasycznej aparatury na rzecz zbudowania własnego pilota z ekranem i systemem operacyjnym Linux (Raspberry Pi).

## 1. Architektura Aparatury

System OpenHD lub standardowa aplikacja GCS (np. QGroundControl) zainstalowana na **Raspberry Pi 4** nie posiada domyślnie "złącz analogowych" potrafiących płynnie i bez opóźnień interpretować pozycję drążków sterowniczych (potencjometrów).

### Konwersja Sygnału Analogowego na USB

Aby drążki zadziałały w systemie Raspberry Pi jako standardowy kontroler (tzw. gamepad USB), musimy użyć pośrednika: **Arduino Pro Micro (ATmega32u4)**.

1. **Drążki (Gimbale Halla):** Z każdego gimbala wychodzą przewody sygnałowe (oś X i oś Y) oraz zasilanie (VCC, GND).
2. **Arduino Pro Micro:** Przewody sygnałowe X i Y lutujemy do pinów analogowych w Arduino (np. A0, A1 dla lewego drążka; A2, A3 dla prawego).
3. **USB:** Arduino łączymy za pomocą kabla USB z portem w Raspberry Pi 4. Na Arduino wgrywamy kod korzystający z biblioteki `Joystick.h`, który przelicza wartości napięcia z drążków na pozycje osi w systemie Windows/Linux.

Dzięki temu po włączeniu Raspberry Pi, widzi on nasz system drążków jako urządzenie `/dev/input/js0`.

## 2. Podłączenie Ekranu

Wybierz ekran dotykowy dedykowany do Raspberry Pi:
- Jeśli to ekran **DSI**, podepnij taśmę do złącza `DISPLAY` na płycie RPi.
- Jeśli to ekran **HDMI**, użyj krótkiego kabla microHDMI-HDMI oraz zasil go z pinów 5V na płytce RPi.

## 3. Odbiór Telemetrii z Drona

Do portu USB w Raspberry Pi podłącz drugi, sparowany moduł **Holybro SiK Radio V3**. 
Będzie on odbierał pakiety MAVLink bezpośrednio od drona, co pozwoli aplikacji QGroundControl na wyświetlanie mapy, baterii oraz horyzontu (sztucznego) w czasie rzeczywistym.

## 4. Zasilanie Pilota

Raspberry Pi 4 wymaga stabilnego zasilania (min. 3A przy 5V).
- W obudowie pilota umieść koszyk na dwa ogniwa litowo-jonowe **18650**.
- Podłącz je do modułu BMS (tzw. Powerbank Board z wyjściem USB 5V 3A).
- Z modułu zasil całe Raspberry Pi krótkim kablem USB-C.

## 5. Druk Obudowy

Zaprojektuj i wydrukuj obudowę posiadającą:
- Centralne miejsce na ekran 5".
- Symetryczne miejsca po lewej i prawej stronie na gimbale drążków.
- Schowek wewnętrzny na Raspberry Pi, Arduino i ogniwa 18650.