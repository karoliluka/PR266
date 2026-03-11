# Analiza slovenskega trga nepremičnin na podlagi Evidence trga nepremičnin v zadnjih 10 letih (ETN)

## Opis problema

Nepremičninski trg je eden ključnih pokazateljev gospodarskega stanja in kakovosti življenja v državi. V Sloveniji so se cene nepremičnin v zadnjih desetih letih močno spremenile in s pomočjo različnih statističnih in analitičnih metod bomo prikazali zakaj.

Cilj projekta je analizirati transakcije nepremičnin v Sloveniji na podlagi odprtih podatkov Evidence trga nepremičnin (ETN), ki jo vodi Geodetska uprava RS. Osredotočili se bomo na **tržne posle** (torej transakcije po tržnih cenah, brez sorodstvenih prenosov, razlastitev ipd.) in poskušali odgovoriti na naslednja vprašanja:

- Kako so se cene nepremičnin (€/m²) gibale skozi čas po posameznih regijah oz. občinah?
- Katere občine oz. lokacije izkazujejo najvišje in najnižje cene na m²?
- Kako se razlikujejo cene glede na vrsto nepremičnine (stanovanje, hiša, garaža, poslovni prostor)?
- Kakšna je tipična površina prodanih nepremičnin po posameznih kategorijah?
- Ali obstaja sezonski vzorec v obsegu in cenah poslov?
- Kateri dejavniki (površina, lokacija, leto izgradnje, vrsta) najbolj vplivajo na ceno?
- Kateri drugi dejavniki (dvetovne krize, vojne, pandemije, ... ) so vplivali na ceno?

---

## Vir in oblika podatkov

**Vir:** [Evidenca trga nepremičnin (ETN)](https://ipi.eprostor.gov.si/jgp/) — Geodetska uprava Republike Slovenije  
**Portal odprtih podatkov:** [podatki.gov.si](https://podatki.gov.si/dataset/evidenca-trga-nepremicnin)

Podatki so javno dostopni in brezplačni prek aplikacije **JGP (Javni geodetski podatki)**. Možen je prenos po posameznem letu in po posamezni občini ali za celo Slovenijo.

### Struktura podatkov

Podatki so v obliki **CSV datotek**, razdeljeni v naslednje sklope:

| Datoteka | Vsebina |
|---|---|
| `*POSLI*.csv` | Datum posla, skupna pogodbena cena (€), tržnost posla, vključenost DDV |
| `*DELISTAVB*.csv` | Lokacija (občina, ulica), vrsta nepremičnine, površina (m²), leto izgradnje, cena dela stavbe |
| `*SIFRANTI*.csv` | Šifranti za kode (vrsta posla, vrsta nepremičnine, tržnost ...) |

Ključna polja za analizo:
- **`POGODBENA_CENA_ODSKODNINA`** — dejanska prodajna cena v €
- **`PRODANA_POVRSINA`** — površina v m²
- **`TRZNOST_POSLA`** — označuje ali gre za tržni posel (filter za analitiko)
- **`DEJANSKA_RABA_DELA_STAVBE`** — vrsta nepremičnine (stanovanje, hiša, pisarna ...)
- **`OBCINA`**, **`NASELJE`**, **`ULICA`** — lokacija
- **`DATUM_SKLENITVE_POGODBE`** — datum transakcije

### Obseg

Podatki so dostopni od leta **2007** dalje, za vsako leto posebej, za posamezno občino ali celotno Slovenijo. Za projekt bomo zajeli obdobje **2015–2025**.

---

## Okvirni plan analize

1. **Pridobitev in čiščenje podatkov** — prenos ETN CSV datotek, združevanje letnikov, filtriranje tržnih poslov, odstranjevanje outlierjev, združitev relevantnih tabel
2. **Eksplorativna analiza** — porazdelitve cen, površin, vrst nepremičnin; časovni trendi
3. **Prostorska analiza** — primerjava po občinah in statističnih regijah
4. **Modeliranje** — regresijski model za napoved cene glede na lokacijo, površino, vrsto in leto
5. **Vizualizacija** — interaktivni grafi in zemljevidi

---
