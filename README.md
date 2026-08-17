# 🐺 WOLF FUEL — Revenue Wolves

Tjedni planer prehrane. Doručak, ručak i večera po danima, tvoj vlastiti meni jela po rubrikama i statistika koliko često jedeš pojedino jelo ili namirnicu (zadnjih 7 / 14 / 30 dana).

Aplikacija radi kao statična web stranica (GitHub Pages), a **baza podataka je JSON datoteka u tvom GitHub repozitoriju** — svaka promjena je git commit, pa imaš i kompletnu povijest plana.

---

## Sadržaj mape

```
wolf-fuel/
├── index.html            ← cijela aplikacija
├── manifest.webmanifest  ← omogućuje instalaciju na iPhone/Mac
├── README.md
└── assets/
    ├── logo-full.svg     ← puni Revenue Wolves logo
    ├── logo-mark.svg     ← glava vuka (koristi se u sučelju)
    ├── icon-192.png / icon-512.png
    ├── apple-touch-icon.png
    └── favicon.png
```

---

## Korak 1 — Objavi aplikaciju (GitHub Pages)

1. Prijavi se na [github.com](https://github.com) i klikni **New repository**.
2. Ime: `wolf-fuel` · vidljivost: **Public** (Pages je besplatan samo za javne repozitorije; u kodu nema ničeg privatnog).
3. Otvori repozitorij → **Add file → Upload files** → povuci **sadržaj** ove mape (`index.html`, `manifest.webmanifest`, `README.md` i mapu `assets`). Klikni **Commit changes**.
   - Napomena: ZIP prvo raspakiraj — GitHub ne raspakirava ZIP automatski.
4. **Settings → Pages** → pod *Build and deployment* odaberi **Deploy from a branch**, grana `main`, mapa `/ (root)` → **Save**.
5. Nakon 1–2 minute aplikacija je na adresi:
   `https://TVOJE-IME.github.io/wolf-fuel/`

Aplikacija odmah radi i bez ičega dalje — podaci se tada čuvaju lokalno u pregledniku. Za dijeljenje između iPhonea i Maca napravi još korake 2 i 3.

---

## Korak 2 — Repozitorij za podatke (tvoja baza)

1. **New repository** → ime: `wolf-fuel-data` · vidljivost: **Private** (tvoj plan prehrane nije javan).
2. Označi **Add a README file** (bitno — repozitorij ne smije biti potpuno prazan) → **Create repository**.

To je sve. Aplikacija će sama stvoriti i ažurirati `data.json` u tom repozitoriju.

---

## Korak 3 — Token (ključ kojim aplikacija piše u tvoju bazu)

1. GitHub → klik na svoj avatar → **Settings** → skroz dolje **Developer settings** → **Personal access tokens → Fine-grained tokens** → **Generate new token**.
2. Postavke tokena:
   - **Token name:** `wolf-fuel`
   - **Expiration:** npr. 1 godina (kad istekne, samo napraviš novi i zalijepiš ga u aplikaciju)
   - **Repository access:** *Only select repositories* → odaberi **wolf-fuel-data**
   - **Permissions → Repository permissions → Contents:** **Read and write** (ništa drugo nije potrebno)
3. **Generate token** i **kopiraj** ga (prikazuje se samo jednom).
4. Otvori aplikaciju → ikona **⚙︎ (Postavke)** → upiši:
   - GitHub korisničko ime
   - Repozitorij: `wolf-fuel-data`
   - Token
   → **Poveži i sinkroniziraj**.
5. Ponovi točku 4 na **svakom uređaju** (iPhone i Mac). Token se sprema isključivo u pregledniku tog uređaja — nikamo se ne šalje osim izravno GitHubu.

> 🔐 Zašto je ovo sigurno razumno: token vrijedi **samo** za `wolf-fuel-data` i **samo** za sadržaj datoteka. Ako ikad posumnjaš da je procurio, obriši ga u GitHub postavkama i napravi novi.

---

## Korak 4 — Instaliraj kao aplikaciju

**iPhone (Safari):** otvori svoju adresu → gumb **Dijeli** (kvadrat sa strelicom) → **Dodaj na početni zaslon**. Dobivaš ikonu vuka i aplikaciju preko cijelog ekrana, bez adresne trake.

**Mac (Safari):** otvori adresu → **File → Add to Dock…**
**Mac (Chrome):** ikona instalacije u adresnoj traci ili ⋮ → *Cast, save and share → Install page as app*.

---

## Kako se koristi

- **Tjedan** — dodirni Doručak / Ručak / Večeru bilo kojeg dana → odaberi jedno ili više jela ili odmah dodaj novo (automatski se veže na tu rubriku). Strelicama listaš tjedne, **⋯** nudi *Kopiraj prošli tjedan* i *Isprazni tjedan*.
- **Jela** — tvoj meni po rubrikama. Svako jelo ima primarnu rubriku, ali ga možeš dodati u bilo koji obrok (npr. jaja i za večeru). Jelu dodaj **namirnice** („jaja, sir, panceta") — statistika ih zbraja kroz sva jela.
- **Statistika** — prekidač 7 / 14 / 30 dana; najčešća jela, namirnice, raznolikost i popis „davno nije na meniju".
- **Postavke (⚙︎)** — sinkronizacija, **Preuzmi sigurnosnu kopiju** / **Učitaj kopiju** (JSON).

---

## Prilagodbe

- **Ime aplikacije:** u `index.html` promijeni tekst u `<title>`, u elementu `.wm` (dva mjesta: topbar i splash) te `BRAND` konstantu na početku skripte; u `manifest.webmanifest` polja `name` i `short_name`.
- **Boje:** sve su u `:root { … }` na vrhu `index.html` (paleta je izvučena iz Revenue Wolves loga).
- **Početna jela:** pri prvom pokretanju ubačeno je tvojih 5 doručaka + „Mamin ručak" — sve se slobodno uređuje ili briše pod **Jela**.

## Ako nešto zapne

| Problem | Rješenje |
|---|---|
| Pages adresa vraća 404 | Pričekaj minutu-dvije nakon prve objave; provjeri da je `index.html` u korijenu repozitorija. |
| Pill „Token?" u vrhu | Token je istekao ili nema *Contents: Read and write* za `wolf-fuel-data` — napravi novi. |
| Pill „Offline" | Nema interneta ili je krivo ime repozitorija — promjene su svejedno spremljene lokalno i sinkronizirat će se kasnije. |
| Promjene s iPhonea ne vidim na Macu | Otvori/fokusiraj aplikaciju (povlači svježe podatke pri povratku u nju), oba uređaja moraju biti povezana na isti repozitorij. |

---

**WOLF FUEL** · Revenue Wolves — nahrani vuka, isplaniraj tjedan.
