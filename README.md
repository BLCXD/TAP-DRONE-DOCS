# Dokumentacja Drona TAP

To repozytorium zawiera całą niezbędną dokumentację do zbudowania drona TAP (urządzenie IoT oparte na ESP32) opisane w projekcie.

## Przegląd

Dron TAP to urządzenie IoT oparte na ESP32, zaprojektowane do operacji poszukiwawczo-ratunkowych, charakteryzujące się:

- **Ramę**: 5-calowa rama cinelifter zdolna do przenoszenia NVIDIA Jetson Orin Nano
- **Kompanijski Komputer AI**: NVIDIA Jetson Orin Nano Developer Kit (8GB) do lokalnego wykrywania obiektów
- **Kontroler Lotu**: Stos SpeedyBee F405 V3/V4 (FC + 4-w-1 ESC 50A)
- **Silniki**: EMAX ECO II 2207 (ok. 1700KV-1900KV dla 6S)
- **Stacja Naziemna (GCS)**: Niestandardowy transmiter oparty na Raspberry Pi 4 z ekranem dotykowym, modułami joysticka i łączem wideo OpenHD
- **Zasilanie**: Bateria LiPo 6S (1300-1500mAh) z BEC do regulacji 5V/12V
- **Komunikacja**: OpenHD (WiFi) lub ExpressLRS do dwukierunkowej telemetrii i wideo

## Struktura Dokumentacji

- `README.md` – Ten plik
- `BOM.md` – Szczegółowa lista materiałów z linkami do polskich sklepów i cenami (~5000 PLN)
- `Build-Instructions.md` – Przewodnik dotyczący montażu mechanicznego, okablowania i elektroniki
- `GCS-Instructions.md` – Instrukcje budowy Stacji Naziemnej (pilota)
- `Software-Setup.md` – Konfiguracja oprogramowania, oprogramowanie AI (YOLO/OpenCV na Jetson) oraz konfiguracja komunikacji
- `3D-Print.md` – Pliki STL i ustawienia druku dla niestandardowych montażów i obudowy