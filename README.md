# Scan Inventory 📦

Aplikacja NativeScript Angular do zarządzania inwentarzem z funkcją skanowania kodów.

## 📱 Opis

Scan Inventory to mobilna aplikacja zbudowana w NativeScript z frameworkiem Angular, umożliwiająca:
- Przeglądanie listy produktów
- Dodawanie nowych produktów z użyciem kamery
- Skanowanie kodów kreskowych/QR
- Edycję i usuwanie produktów
- Zarządzanie ustawieniami aplikacji

## 🎯 Funkcjonalności

### Widoki (4 ekrany)
1. **Lista produktów** - główny widok z listą wszystkich produktów
   - Wyszukiwarka produktów
   - Status produktów (dostępny, niski stan, brak)
   - Pull-to-refresh
   - FAB do dodawania nowych produktów

2. **Szczegóły produktu** - pełne informacje o produkcie
   - Zdjęcie produktu
   - Kod produktu
   - Status i ilość
   - Akcje: edycja, usuwanie, zmiana ilości

3. **Dodaj/Edytuj produkt** - formularz z walidacją
   - Nazwa, kod, kategoria, ilość, opis
   - Skanowanie kodu kamerą 📷
   - Robienie zdjęcia produktu
   - Walidacja pól formularza

4. **Ustawienia** - konfiguracja aplikacji
   - Tryb offline
   - Automatyczna synchronizacja
   - Ciemny motyw
   - Dźwięki i wibracje skanera
   - Zarządzanie danymi

### Funkcja natywna: Kamera 📸
Aplikacja wykorzystuje natywną kamerę urządzenia do:
- **Skanowania kodów** - szybkie wprowadzanie kodów produktów
- **Robienia zdjęć** - dokumentacja wizualna produktów
- **Sprawdzania uprawnień** - obsługa uprawnień do kamery

### Integracja z API
- **GET** - pobieranie listy produktów
- **POST** - tworzenie nowych produktów
- **PUT** - aktualizacja produktów
- **DELETE** - usuwanie produktów
- **Obsługa błędów** - informowanie użytkownika o problemach
- **Tryb offline** - lokalne przechowywanie danych

## 🛠️ Technologie

- **NativeScript** ~8.6.0
- **Angular** ~17.1.0
- **TypeScript** ~5.3.0
- **RxJS** ~7.8.0
- **@nativescript/camera** ~5.1.0

## 📋 Wymagania

- Node.js 18+
- NativeScript CLI (`npm install -g nativescript`)
- Xcode (dla iOS)
- Android Studio (dla Android)

## 🚀 Instalacja i uruchomienie

### 1. Instalacja zależności
```bash
npm install
```

### 2. Uruchomienie na iOS
```bash
ns run ios
```

### 3. Uruchomienie na Android
```bash
ns run android
```

### 4. Preview (bez emulatora)
```bash
ns preview
```

## 📁 Struktura projektu

```
scan-inventory/
├── src/
│   ├── app/
│   │   ├── features/
│   │   │   ├── products/
│   │   │   │   ├── product-list/      # Lista produktów
│   │   │   │   ├── product-detail/    # Szczegóły produktu
│   │   │   │   └── product-add/       # Dodawanie/edycja produktu
│   │   │   └── settings/              # Ustawienia
│   │   ├── models/
│   │   │   └── product.model.ts       # Model produktu
│   │   ├── services/
│   │   │   ├── product.service.ts     # Serwis API produktów
│   │   │   ├── camera.service.ts      # Serwis kamery
│   │   │   └── storage.service.ts     # Serwis lokalnego storage
│   │   ├── app.component.ts
│   │   ├── app.module.ts
│   │   └── app-routing.module.ts
│   ├── app.css                        # Globalne style
│   └── main.ts                        # Punkt wejściowy
├── App_Resources/                     # Zasoby natywne
├── package.json
├── nativescript.config.ts
├── tsconfig.json
└── README.md
```

## 📸 Zrzuty ekranu

### Lista produktów
- Wyświetlanie wszystkich produktów
- Kolorowe statusy (zielony/pomarańczowy/czerwony)
- Przycisk skanowania w pasku wyszukiwania

### Szczegóły produktu
- Pełne informacje o produkcie
- Zdjęcie produktu
- Przyciski akcji (edycja, usuwanie)

### Dodawanie produktu
- Formularz z walidacją
- Przycisk skanowania kodu
- Możliwość zrobienia zdjęcia

### Ustawienia
- Przełączniki funkcji
- Status połączenia API
- Zarządzanie danymi

## ✅ Definition of Done

- [x] 4 widoki z nawigacją (Lista, Szczegóły, Dodaj/Edytuj, Ustawienia)
- [x] Funkcja natywna - kamera do skanowania i zdjęć
- [x] Integracja z API (GET/POST/PUT/DELETE)
- [x] Walidacja formularza (wymagane pola, min/max length)
- [x] Obsługa błędów (brak połączenia, błędy API)
- [x] README.md z dokumentacją
- [x] Struktura projektu gotowa do commitów

## 🔧 Konfiguracja

### Uprawnienia iOS (Info.plist)
```xml
<key>NSCameraUsageDescription</key>
<string>Aplikacja wymaga dostępu do kamery do skanowania kodów i robienia zdjęć produktów.</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>Aplikacja wymaga dostępu do galerii do wyboru zdjęć produktów.</string>
```

### Uprawnienia Android (AndroidManifest.xml)
```xml
<uses-permission android:name="android.permission.CAMERA"/>
<uses-feature android:name="android.hardware.camera" android:required="false"/>
```

## 📝 API Endpoints

| Metoda | Endpoint | Opis |
|--------|----------|------|
| GET | /products | Pobiera listę produktów |
| GET | /products/:id | Pobiera szczegóły produktu |
| POST | /products | Tworzy nowy produkt |
| PUT | /products/:id | Aktualizuje produkt |
| DELETE | /products/:id | Usuwa produkt |

## 🧪 Testowanie

### Testowanie lokalne
1. Uruchom na emulatorze lub urządzeniu
2. Dodaj produkt z użyciem funkcji skanowania
3. Sprawdź czy produkt pojawia się na liście
4. Przetestuj edycję i usuwanie
5. Sprawdź zachowanie przy braku połączenia

### Scenariusze testowe
- [ ] Dodawanie produktu z zeskanowanym kodem
- [ ] Robienie zdjęcia produktu
- [ ] Walidacja formularza (puste pola, za krótkie nazwy)
- [ ] Pull-to-refresh na liście
- [ ] Wyszukiwanie produktów
- [ ] Obsługa błędów API

## 👤 Autor

Developer - Projekt zaliczeniowy NativeScript Angular

## 📄 Licencja

MIT License

