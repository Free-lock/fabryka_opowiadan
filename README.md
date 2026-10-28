📖 StoryCraft — Generator opowiadań z ilustracjami AI
Aplikacja w Pythonie i Streamlit, która zamienia pomysł użytkownika w opowiadanie z ilustracjami generowanymi przez OpenAI.

StoryCraft prowadzi przez cały proces twórczy: od zarysu fabuły, przez planowanie scen i redakcję tekstu, po generowanie ilustracji oraz eksport gotowej historii.

✨ Funkcje
🔐 Korzystanie z własnego klucza API OpenAI.
🤖 Pobieranie listy modeli dostępnych na koncie użytkownika.
📏 Wybór docelowej długości opowiadania: 1500–4000 słów, co 500.
🎭 Konfiguracja gatunku, grupy wiekowej i typu zakończenia.
🦸 Definiowanie imienia, wyglądu i charakteru bohatera.
📝 Generowanie oraz edycja tytułu i zarysu fabuły.
🎬 Planowanie 4–8 najważniejszych scen.
📖 Generowanie opowiadania scena po scenie i edycja gotowego tekstu.
🎨 Tworzenie ilustracji do wybranych scen.
🖼️ Wybór stylu i jakości ilustracji.
💾 Zapis kompletnego projektu do pliku JSON.
📂 Wczytywanie projektu i kontynuowanie pracy.
📄 Eksport do PDF z polskimi znakami i ilustracjami umieszczonymi w tekście.
☁️ Możliwość uruchomienia lokalnie lub na Streamlit Community Cloud.
🛠️ Technologie
Technologia	Zastosowanie
Python 3.11	Logika aplikacji
Streamlit	Interfejs użytkownika
OpenAI API	Generowanie tekstów i ilustracji
Pydantic	Walidacja danych i plików projektu
Pillow	Przetwarzanie ilustracji
fpdf2	Generowanie dokumentów PDF
Aplikacja nie wymaga bazy danych. Projekt jest przechowywany w bieżącej sesji, a użytkownik może pobrać jego kopię jako plik JSON.

📁 Struktura projektu
storycraft/
├── app.py
├── requirements.txt
├── README.md
├── .streamlit/
│   └── config.toml
└── fonts/
    ├── DejaVuSans.ttf
    └── DejaVuSans-Bold.ttf
Fonty DejaVu Sans umożliwiają poprawny eksport polskich znaków do PDF. Można je pobrać ze strony DejaVu Fonts.

Zalecane jest umieszczenie obu plików fontów w repozytorium, aby aplikacja nie zależała od fontów zainstalowanych na serwerze. Przy ich dystrybucji należy zachować odpowiednią informację licencyjną dostarczoną z fontami.

🚀 Uruchomienie lokalne
1. Pobierz projekt
Sklonuj repozytorium lub pobierz jego zawartość, a następnie przejdź do katalogu projektu.

2. Utwórz środowisko wirtualne
python -m venv .venv
Upewnij się, że używasz Pythona 3.11.

3. Aktywuj środowisko
Windows — PowerShell:

.venv\Scripts\Activate.ps1
Linux / macOS:

source .venv/bin/activate
4. Zainstaluj zależności
python -m pip install -r requirements.txt
Przykładowa zawartość requirements.txt:

streamlit>=1.46,<2
openai>=1.68,<3
pydantic>=2.8,<3
fpdf2>=2.8,<3
Pillow>=10,<13
Uwaga: nie instaluj jednocześnie pakietów fpdf i fpdf2. Projekt korzysta z fpdf2, mimo że import w kodzie ma postać from fpdf import FPDF.

5. Uruchom aplikację
streamlit run app.py
Domyślnie aplikacja będzie dostępna pod adresem:

http://localhost:8501
⚙️ Konfiguracja Streamlit
Utwórz plik .streamlit/config.toml:

[server]
maxUploadSize = 50

[theme]
primaryColor = "#8B5CF6"
backgroundColor = "#FFFFFF"
secondaryBackgroundColor = "#F5F3FF"
textColor = "#1E1B4B"
font = "sans serif"
Limit przesyłanych plików wynosi 50 MB. Aplikacja dodatkowo sprawdza rozmiar i strukturę wczytywanego projektu.

🔑 Klucz API i dostęp do modeli
Do generowania treści wymagany jest klucz API z OpenAI Platform.

Po uruchomieniu aplikacji:

Wklej klucz w polu „Klucz API” w panelu bocznym.
Wybierz model tekstowy.
Wybierz model ilustracji.
Ustaw docelową długość historii.
Lista modeli jest pobierana z konta OpenAI i filtrowana pod kątem zastosowań aplikacji. Samo pojawienie się modelu na liście nie gwarantuje dostępu ani zgodności z używanym endpointem API.

Niektóre modele obrazowe mogą wymagać weryfikacji organizacji w OpenAI.

Generowanie tekstów i obrazów jest płatne według cennika API OpenAI. Abonament ChatGPT nie pokrywa kosztów API.

🧭 Jak korzystać?
1. 💡 Pomysł
Podaj:

tematykę opowiadania,
grupę wiekową,
gatunek,
imię lub nazwę bohatera,
opis bohatera,
typ zakończenia,
liczbę scen.
Następnie wygeneruj tytuł i zarys fabuły.

2. 📝 Tytuł i opis
Sprawdź propozycję i wprowadź poprawki. Po zatwierdzeniu aplikacja przygotuje plan scen.

3. 🎬 Sceny
Dostosuj tytuły i opisy najważniejszych wydarzeń. Na ich podstawie powstanie pełne opowiadanie.

4. 📖 Opowiadanie
Przeczytaj tekst i wprowadź własne zmiany. Aplikacja pokazuje rzeczywistą liczbę słów.

Wybrana długość jest celem generowania, a nie gwarancją dokładnej liczby słów.

5. 🎨 Ilustracje
Wybierz:

sceny do zilustrowania,
styl graficzny,
jakość obrazów.
Każda ilustracja jest generowana osobnym żądaniem API. Aplikacja generuje brakujące obrazy, zachowując istniejące.

6. 📦 Podgląd i eksport
Przejrzyj projekt, a następnie:

pobierz JSON, aby zachować możliwość dalszej edycji,
przygotuj i pobierz PDF do czytania lub drukowania.
Przed przejściem do innego etapu zapisz zmiany przyciskiem w formularzu. Niezatwierdzone zmiany nie są częścią eksportowanego projektu.

🖼️ Ilustracje w PDF
Domyślnie ilustracje są umieszczane po tekście sceny, której dotyczą. Aplikacja rozpoznaje sceny na podstawie ich tytułów występujących w osobnych wierszach opowiadania.

Możesz również wskazać dokładne miejsce ilustracji, dodając w tekście znacznik:

Bohaterka ostrożnie otworzyła drzwi do tajemniczego ogrodu.

[[ILUSTRACJA:1]]

Za progiem czekał na nią świat, którego nigdy wcześniej nie widziała.
Znacznik [[ILUSTRACJA:1]] oznacza ilustrację do pierwszej sceny, a [[ILUSTRACJA:2]] — do drugiej.

Ręczny znacznik ma pierwszeństwo przed automatycznym rozmieszczeniem.
Znaczniki nie są widoczne w PDF.
Jeśli nie można rozpoznać scen ani znaleźć znaczników, odpowiednie obrazy trafiają na koniec dokumentu z komunikatem ostrzegawczym.
Duża ilustracja może zostać przeniesiona na kolejną stronę, aby zmieściła się razem z podpisem.
Znaczniki najlepiej dodać przed generowaniem ilustracji, ponieważ zapis zmienionego tekstu usuwa dotychczasowe obrazy.

💾 Zapis i wczytywanie projektu
Format JSON
Plik projektu zawiera:

wersję formatu,
ustawienia opowiadania,
tytuł i zarys,
plan scen,
pełny tekst,
ilustracje zapisane jako base64,
informacje o użytych modelach.
Plik jest samowystarczalny — nie wymaga osobnego folderu z obrazami. Można zapisać również projekt, który nie został jeszcze ukończony.

Klucz API nie jest zapisywany w JSON ani PDF.

Wczytywanie
Otwórz sekcję „Wczytaj projekt JSON” w panelu bocznym.
Wybierz plik pobrany wcześniej z aplikacji.
Kliknij „Wczytaj projekt”.
Kontynuuj edycję lub eksportuj dokument.
Wczytanie projektu zastępuje bieżącą pracę w sesji. W razie potrzeby najpierw pobierz aktualny projekt.

Limity importu
Projekt JSON: do 50 MB.
Pojedyncza ilustracja: do 8 MB.
Wymiary ilustracji: maksymalnie 4096 × 4096 pikseli.
Obsługiwane obrazy: nieanimowane PNG, JPEG i WEBP.
🔄 Zależności między etapami
Zmiana wcześniejszych założeń może unieważnić wyniki kolejnych etapów:

Zmiana	Usuwane wyniki
Wygenerowanie nowego zarysu	Sceny, tekst i ilustracje
Zapis zmienionego tytułu lub opisu	Sceny, tekst i ilustracje
Zapis zmienionego planu scen	Tekst i ilustracje
Zapis zmienionego opowiadania	Ilustracje
Pozwala to uniknąć pozostawienia obrazów lub tekstów niezgodnych z aktualną wersją historii.

☁️ Wdrożenie na Streamlit Community Cloud
Umieść projekt w repozytorium GitHub.
Dodaj app.py, requirements.txt, konfigurację Streamlit i fonty.
Zaloguj się do Streamlit Community Cloud.
Utwórz aplikację, wskazując repozytorium i plik app.py.
Wybierz Python 3.11 w ustawieniach wdrożenia, jeśli jest dostępny.
Uruchom wdrożenie.
Klucz OpenAI jest podawany przez użytkownika w interfejsie — nie trzeba umieszczać go w repozytorium ani w konfiguracji aplikacji.

🛡️ Prywatność i bezpieczeństwo
Klucz OpenAI jest używany w bieżącej sesji aplikacji.
Projekty nie są zapisywane w bazie danych aplikacji.
Treści i instrukcje ilustracji są przesyłane do OpenAI w celu realizacji żądań.
Wczytany JSON przechodzi walidację struktury, limitów i obrazów.
Plik JSON zawiera pełną treść oraz ilustracje — traktuj go jak prywatny dokument.
Nie podawaj danych poufnych i nie dodawaj kluczy API do repozytorium.
Brak zapisu do bazy nie oznacza, że dane są przetwarzane wyłącznie na urządzeniu użytkownika: aplikacja Streamlit i API OpenAI uczestniczą w ich przetwarzaniu.

⚠️ Ograniczenia
Brak automatycznego zapisu. Utrata lub zakończenie sesji może spowodować utratę niezapisanej pracy.
Długość wygenerowanego opowiadania może odbiegać od wybranego celu.
Wygląd bohaterów może różnić się między niezależnie generowanymi ilustracjami.
Dostępność modeli, parametry i ceny zależą od OpenAI.
Wyższa jakość ilustracji zwykle zwiększa koszt i czas generowania.
Font DejaVu Sans obsługuje polskie znaki, ale nie wszystkie emoji i znaki innych alfabetów.
Treści wygenerowane przez AI wymagają sprawdzenia, szczególnie gdy są przeznaczone dla dzieci.
🧩 Rozwiązywanie problemów
API odrzuca generowanie ilustracji
Rozwiń szczegóły błędu w aplikacji. Sprawdź:

dostęp do modelu obrazowego,
ewentualną konieczność weryfikacji organizacji,
uprawnienia klucza API,
zgodność modelu z parametrami żądania.
Błąd 401
Sprawdź poprawność klucza API.

Błąd 429
Sprawdź środki, limity rozliczeniowe oraz limity liczby żądań na koncie OpenAI.

PDF nie generuje się
Upewnij się, że w katalogu fonts/ znajdują się:

DejaVuSans.ttf
DejaVuSans-Bold.ttf
Sprawdź również, czy zainstalowano fpdf2, a nie starszy pakiet fpdf.

Ilustracja pojawia się na końcu PDF
Przywróć tytuły scen w osobnych wierszach albo użyj znacznika [[ILUSTRACJA:n]] w wybranym miejscu tekstu.

Projekt zniknął po zamknięciu aplikacji
Aplikacja nie zapewnia trwałego przechowywania projektów. Aby zachować pracę, pobierz JSON przed zakończeniem sesji.

📖 Od pierwszego pomysłu do własnej ilustrowanej historii.