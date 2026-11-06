## Spis treści
1. [Wprowadzenie i Cel Biznesowy](#wprowadzenie-i-cel-biznesowy)
2. [Architektura Systemu](#architektura-systemu)
3. [Stos Technologiczny](#stos-technologiczny)
4. [Zakres Prac (MoSCoW)](#zakres-prac-moscow)
5. [Analiza Ryzyka i Mitygacja](#analiza-ryzyka-i-mitygacja)
6. [Harmonogram Realizacji](#harmonogram-realizacji)

---

## 1. Wprowadzenie i Cel Biznesowy
Projekt ma na celu podniesienie poziomu bezpieczeństwa teleinformatycznego w firmie klienta poprzez odejście od płaskiej struktury sieciowej i wdrożenie segmentacji opartej na wirtualnych sieciach LAN (VLAN) oraz centralnej zaporze sieciowej OPNsense.

## 2. Architektura Systemu
- **Brama / Firewall:** OPNsense odpowiada za routing między podsieciami oraz filtrację ruchu do sieci WAN.
- **Łączność:** Połączenie router-switch zrealizowane jako port Trunk (802.1Q).
- **Strefy bezpieczeństwa:**
  - `VLAN 10 (Biuro)` – bezpieczna sieć stacji roboczych pracowników.
  - `VLAN 20 (Serwery)` – izolowana strefa zasobów krytycznych (NAS, aplikacje).
  - `VLAN 30 (Goście)` – dostęp wyłącznie do zasobów publicznych (Internet), bez dostępu do sieci lokalnej firmy.

## 3. Stos Technologiczny
- **Firewall:** OPNsense
- **Symulacja / Testy:** EVE-NG / VirtualBox
- **Dokumentacja:** Draw.io
- **Repozytorium:** GitHub

## 4. Zakres Prac (MoSCoW)
- **Must:** Konfiguracja VLAN, OPNsense, reguły izolacji ruchu gości.
- **Should:** Izolacja klientów w sieci Wi-Fi, usługi DHCP per VLAN.
- **Could:** Captive Portal.
- **Won't:** Klaster HA OPNsense.

## 5. Analiza Ryzyka i Mitygacja
1. *Błędy w regułach zapory blokujące poprawny ruch biurowy* -> P=2, W=3 (Niski) -> Weryfikacja w środowisku symulacyjnym przed wdrożeniem.
2. *Utrata konfiguracji urządzenia* -> P=2, W=4 (Średni) -> Regularny backup plików konfiguracyjnych `.xml` archiwizowany w tym repozytorium.

## 6. Harmonogram Realizacji
- **Etap 1 (Koncept i Założenia):** Zatwierdzenie architektury i zakresu prac przez klienta.
- **Etap 2 (Konfiguracja środowiska testowego):** Symulacja układu i reguł bezpieczeństwa.
- **Etap 3 (Finalne wdrożenie i przekazanie):** Dokumentacja końcowa i akceptacja przez zamawiającego.
