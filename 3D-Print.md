# Instrukcje i Wskazówki do Druku 3D

Projekt posiada kilka bardzo specyficznych części, które muszą zostać wydrukowane z odpowiednich materiałów. Zwykłe PLA ulegnie stopieniu (lub odkształceniu) ze względu na wysoką temperaturę silników i elektroniki, szczególnie układu NVIDIA Jetson Orin Nano.

## Zestawienie Części

| Nazwa Części | Zalecany Materiał | Wypełnienie | Opis i Wskazówki |
|--------------|-------------------|-------------|------------------|
| **Upper Deck (Nadbudówka Jetson)** | PETG / ABS / PC | Min. 40% (Triangles) | Górna platforma mocowana na dachu ramy, zapewniająca odpowiednio szeroką bazę (ok. 100x80mm) do przykręcenia Jetsona. |
| **Wibroizolatory (Dampers)** | TPU (Elastyczny) | 100% | Gumki / Podkładki umieszczane między pokładem a Jetsonem w celu redukcji drgań od silników 2207, chroniące procesor. |
| **Uchwyt Kamery FPV** | TPU (Elastyczny) | 20-30% | Miękkie mocowanie kamery pochłaniające uderzenia podczas ewentualnych twardych lądowań (tzw. "Jello killer"). |
| **Obudowa Pilota (GCS)** | PLA / PETG | 15-20% (Grid) | Wieloelementowa obudowa do skręcenia na śruby M3. Zawiera gniazda na Gimbale Halla, ekran dotykowy, Raspberry Pi 4 i koszyk na baterie 18650. |
| **Uchwyty Anten (SiK Radio)**| TPU / PETG | 100% | Montaże zabezpieczające delikatne anteny telemetrii w kształcie litery V, ułatwiające dobrą propagację fal. |

## Parametry Druku

- **PETG (Politereftalan etylenu z glikolem):** Temp. dyszy: ~235°C, Temp. stołu: ~75°C. Wymaga lekkiego chłodzenia. Bardzo dobra wytrzymałość na temperaturę i pękanie, co sprawia, że nadaje się idealnie do konstrukcji drona i ochrony elektroniki.
- **TPU (Elastomer):** Temp. dyszy: ~220°C, Temp. stołu: ~60°C. Wyłącz retrakcję (lub ustaw ją na minimum) i drukuj bardzo wolno (np. 15-20 mm/s), zwłaszcza jeśli używasz ekstrudera typu Bowden.
- **PLA:** Można wykorzystać wyłącznie do obudowy pilota, ponieważ pilot nie generuje ekstremalnych wibracji ani drastycznie wysokich temperatur. W lecie jednak zostawienie pilota z PLA na słońcu może spowodować zmiękczenie plastiku.

## Kontrola Jakości

Po wydrukowaniu upewnij się, że:
1. Śruby M3 wkręcają się z odpowiednim oporem (możesz zastosować gwintowane inserty mosiężne wtapiane lutownicą dla najwyższej trwałości, zwłaszcza w obudowie pilota).
2. Górna nadbudówka dla Jetsona nie styka się bezpośrednio z kręcącymi się śmigłami 5-calowymi. Środek ciężkości powinien być dokładnie weryfikując na etapie modelowania CAD.