# 📖 Jak zrobić **custom prefixy** na serwerze Minecraft za pomocą Resource Packa?

Dobra wiadomość – to jest **bardzo proste**, zrobisz to w **maksymalnie 5 minut**, a co najważniejsze – **nie potrzebujesz do tego żadnego pluginu**!  

---

## 🖌️ Krok 1: Stwórz własne tekstury prefixów

Możesz je przygotować w dowolnym programie graficznym (np. Photoshop, GIMP, Paint.NET, libresprite, asperite, blockbench).  
Maksymalny zalecany wymiar: **256x256**

Dla przykładu zrobiłem 4 proste prefixy:
| Ranga      | Wymiary Textury | Custom Znak | Textura Prefixu |
|-----------|---------|-------------|--------|
| **Właściciel** | 91×16 | ᜀ | ![obraz](https://github.com/user-attachments/assets/806ef04f-92a1-4480-a0c1-245ee7724185) |
| **Moderator** | 79×16 | ᜁ | ![obraz](https://github.com/user-attachments/assets/5cf5a056-3ecd-4968-b1eb-dae54fc78554) |
| **VIP**        | 75×16 | ᜂ| ![obraz](https://github.com/user-attachments/assets/80da3696-c153-411e-95df-e80ead225abf) |
| **Gracz**      | 87×16 | ᜃ | ![obraz](https://github.com/user-attachments/assets/4fdb46a1-31b1-4de5-b3c9-3719414fda27) |


---

## 📂 Krok 2: Dodaj tekstury do Resource Packa

1. Pobierz gotowego Resource Packa, którego wysłałem wcześniej.  
2. Otwórz go i przejdź do:  
   **`assets/jakubprefix/textures/prefix`**
3. Wgraj tam swoje textury (w formacie **.png**).

---

## 📝 Krok 3: Skonfiguruj `default.json`

Przejdź do:  
**`assets/minecraft/font/default.json`**  
i otwórz plik. Znajdziesz tam mapowanie znaków na obrazki.

Dodaj swoje prefixy, trzymając się tego formatu:  
> [Lista przykładowych znaków do użycia](https://jrgraphix.net/r/Unicode/E000-F8FF)

```jsonc
{
    "providers": [
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/root.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜀ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/moderator.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜁ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/vip.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜂ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/gracz.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜃ"]
        }
    ]
}
```

---

## ⚙️ Parametry `ascent` i `height`

- **`ascent`** – Odpowiada za położenie textury (w poionie)
- **`height`** – Odpowiada za wielkość textury

🔧 Zalecane wartości: **7 / 8**

Gotowy efekt na chacie:  
<img width="439" height="18" alt="358780551-aaa07922-7122-47e5-ab4b-0e9342c1fcec" src="https://github.com/user-attachments/assets/2700c185-3226-4386-aa04-143de6838b41" />



> ⚠️ **Uwaga:** nie ustawiaj zbyt dużych wartości – zbyt wysokie wartości mogą spowodować nieprawidłowe załadowanie textury

---

## 🌐 Krok 4: Wgraj Resource Pack na hosting

Najprościej skorzystać z [mc-packs.net](https://mc-packs.net/).  
Upewnij się, że resourcepack jest zapakowany w formacie **.zip**.

---

## 🛠️ Krok 5: Konfiguracja serwera

1. Otwórz plik `server.properties`
2. Znajdź i zmodyfikuj poniższe linie:

```properties
require-resource-pack=true
resource-pack=https://download.mc-packs.net/pack/baf77fd7bbc3b735975db419368851796885370a.zip
resource-pack-sha1=baf77fd7bbc3b735975db419368851796885370a
```

- Pierwsza linia wymusza włączenie paczki.
- Druga linia to link do paczki.
- Trzecia linia to hash SHA-1.

---

# ⚠️ Możliwe błędy/problemy/przydatne informacje

**1. Textura zostanie zabarwiona (np po kolorze nicku, czy chatu)**

<img width="412" height="18" alt="358780847-d445d342-a27d-4fa4-a08f-412c91809e8f" src="https://github.com/user-attachments/assets/e3a5a2e3-d217-4c3c-8d6a-664aa33a13cf" />
``Aby uniknąć tego problemu kolor prefixu musi zostać zresetowany (<white>/<reset>/&f/&r/§f/§r)``

**2. Gracze odnajdą twój znak** 

Jeżeli gracze znajdą twój znak będą mogli nim zaspamić chat, co by mogło zniszczyć jego czytelność.

``Aby rozwiązać problem, należy pobrać dowolny plugin na blokadę słów/znaków, przykładowo [chatmanagera](https://modrinth.com/plugin/chatmanager)``

**3. Ikonka mimo prawidłowej ścieżki się nie pojawia**

``Aby rozwiązać ten problem, sprawdź czy textura w nazwie nie ma spacji, jest w formacie .png, nie zawiera polskich znaków, nie zawiera dużych znaków, oraz ma rozmiar mniejszy niż 256``

**4. Ładowanie resourcepacka po dołączeniu na serwer proxy**

Jeżeli chcesz, aby gracze ładowali texturepack już z poziomu serwera proxy to zainstaluj plugin [forcepack](https://github.com/SamB440/ForcePack/releases). Pozwoli to między innymi na jednoczesne przeładowanie resourcepacka dla każdego gracza na sieci, a nie tylko na konkretnym serwerze.

# Poradnik do tworzenia custom gui

⚠️ Poradnik jest w trakcie tworzenia


