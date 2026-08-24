# Budowa Drona - Instrukcja Mechaniczna i Elektryczna

Dron ratowniczy projektowany na konkurs "Naukolatek" wymaga zmieszczenia układu Jetson Orin Nano na 5-calowej ramie.

## 1. Wybór i Montaż Ramy

1. Złożenie ramy 5-calowej (np. TBS Source One V5).
2. Na dolnym pokładzie (Bottom Plate) montujemy "stos" z kontrolerem lotu SpeedyBee F405 V3 (rozstaw śrub 30.5x30.5mm).
3. Na górnym pokładzie (Top Plate) konieczne będzie wydrukowanie w technologii 3D specjalnego "Upper Deck'a" (podstawki), który pozwoli na przykręcenie płyty bazowej układu NVIDIA Jetson Orin Nano (wymiary modułu to ok. 100x80mm). 
   - *Uwaga:* Pomiędzy Jetsonem a drukiem 3D zastosuj gumowe wibroizolatory (dumpery), aby wstrząsy silników EMAX nie uszkodziły płyty głównej komputera AI.

## 2. Montaż Silników EMAX ECO II 2207

1. Przymocuj 4 silniki EMAX ECO 2207 na końcach ramion za pomocą śrub M3 (zazwyczaj o długości 7-8mm dla grubości ramienia 5mm). Użyj kleju do gwintów (niebieski Loctite).
2. Poprowadź kable silników (trzy żyły) do regulatora ESC 4w1 (znajdującego się na dole stosu SpeedyBee).
3. Przylutuj kable do padów ESC, pilnując, aby izolacja kabli nie przecierała się o ostre krawędzie ramy (carbon przewodzi prąd!).

## 3. Zasilanie i Elektronika

### Zasilanie główne

1. Wlutuj główny kabel XT60 z kondensatorem Low-ESR (1000uF 35V) do padów zasilających na regulatorze ESC.
2. Podłącz regulator ESC z kontrolerem lotu FC (SpeedyBee) za pomocą dołączonej wtyczki wielopinowej.

### Zasilanie NVIDIA Jetson

Jetson Orin Nano wymaga zasilania rzędu 5V-19V (najlepiej z zasilacza 9V-12V, zużycie ok. 15W pod obciążeniem).
1. Ponieważ pakiety 6S dostarczają od 22.2V do 25.2V, musisz użyć potężnego reduktora napięcia (tzw. przetwornicy BEC Step-Down), który obsłuży prąd 3A przy np. 12V.
2. Wejście BEC-a lutujemy do padów baterii w FC, a wyjście (12V) prowadzimy bezpośrednio do wtyku zasilania (Barrel Jack) na płycie Jetsona.

### Podłączenie Kamery i Telemetrii

1. Kamerę RunCam Night Eagle 3 podłączamy przewodem sygnałowym (CSI lub ewentualnie USB) do układu Jetson (to Jetson będzie przetwarzał obraz i wysyłał go dalej). Jeśli kamera jest analogowa, obraz musi być przetworzony cyfrowo przez tzw. grabber obrazu na USB.
2. Moduł radiowy **Holybro SiK Radio V3** (telemetria) łączymy z wolnym portem UART w kontrolerze SpeedyBee F405 (TX do RX, RX do TX, zasilanie 5V).

## 4. Środek Ciężkości (CG)

Upewnij się, że bateria LiPo (umieszczona zazwyczaj na dachu lub pod brzuchem drona) równoważy ciężar modułu Jetson, tak aby środek ciężkości wypadał idealnie pośrodku kontrolera lotu.