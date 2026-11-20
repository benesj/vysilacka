# Vysílačka v2 – tisk a montáž

Tiskárna: Prusa MK4 (podložka 250 × 210 mm). Všech 16 dílů se na ni vejde a žádný nepotřebuje podpěry. Obrázkový montážní návod (16 stran A4) máš zvlášť v Claudovi, odtud ho exportuješ do PDF.

Složky:
- `3MF/` – **hotové tiskové desky** `deska_1.3mf` až `deska_8.3mf`, díly už rozmístěné na podložce MK4. Stačí otevřít v PrusaSliceru, zvolit filament a slicovat (deska 8 je TPU). Kdyby se PrusaSlicer zeptal, jestli načíst díly jako jeden objekt, zvol Ne.
- `STL/` – díly k tisku jednotlivě, už natočené pro tisk (číslo, název a materiál jsou v názvu souboru),
- `STEP/` – stejné díly pro úpravy v CAD a celá sestava `00_sestava_vysilacka_v2.step` (otevřeš ji ve FreeCADu),
- `zdroj/` – parametrický model v Pythonu (CadQuery), ze kterého se dá všechno přegenerovat.

## 1. Tisk

Rozdělení na desky:

| Deska | Díly | Materiál | Podložka |
|---|---|---|---|
| 1 | 01 tělo levé + 13, 14, 15 úchyty + 11, 12 knoflíky | ASA | texturovaná |
| 2 | 02 tělo pravé | ASA | texturovaná |
| 3 | 04 víko levé | ASA | texturovaná |
| 4 | 05 víko pravé | ASA | texturovaná |
| 5 | 03 rámeček displeje | ASA | libovolná |
| 6 | 06 deska stínítka + 07, 08 lišty displeje | ASA | libovolná |
| 7 | 09, 10 dvířka | ASA | libovolná |
| 8 | 16 opěrka | TPU 95A | hladká PEI |

Doporučené nastavení pro ASA (PrusaSlicer, tryska 0,4 mm, box zavřený):
- výška vrstvy 0,20 mm (rámeček a dvířka klidně 0,15 mm kvůli vzhledu),
- 4 perimetry, 5 horních a spodních vrstev, výplň 25 % gyroid,
- **úchyty 13, 14, 15 a knoflíky 11, 12 s výplní 100 %**: v PrusaSliceru klikni na díl pravým tlačítkem, zvol Přidat nastavení → Výplň a nastav 100 %,
- podpěry: **žádné**, brim 5 mm u těla a víka,
- šev (seam): zarovnaný, zadní strana.

TPU (deska 8): pomalu, asi 25 mm/s, bez retrakcí nebo s minimálními.

Díly jsou navržené tak, aby se tiskly bez podpěr. Malé otvory a okénka tiskárna přemostí sama. Kdyby PrusaSlicer přece jen na nějakém místě hlásil převis, zapni *Podpěry → Jen na podložce*. Podpěry se pak jen odlomí.

**Nejdřív vytiskni zkušební díly:** jeden boční úchyt (13) a oba knoflíky (11, 12). Hned podle nich ověříš, jestli sedí zalisovací matice, šrouby a karabinka klíčenky, a teprve potom tiskni velké díly.

## 2. Spojovací materiál

| Položka | Kusů | Kam |
|---|---|---|
| Zalisovací (heat-set) matice M3, délka 5–6 mm, otvor 4,0 mm | 28 (+ rezerva) | spoj polovin 4, víko 8, rámeček 8, boční úchyty 6, opěrka 2 |
| Šroub M3×8, válcová hlava (DIN 912) | 14 | spoj polovin 4, víko 8, opěrka 2 |
| Šroub M3×8, půlkulatá hlava (ISO 7380) | 8 | rámeček zepředu |
| Šroub M3×20 (DIN 912) | 8 | hlavní pant stínítka 2, boční úchyty 6 (z toho 2 jsou čepy) |
| Šroub M3×16 (DIN 912) | 4 | hlavní úchyt skrz rámeček a čelo |
| Šroub M3×25 (DIN 912) | 1 | čep hlavního úchytu |
| Matice M3 pojistná (DIN 985, nylon) | 7 | pant 2, hlavní úchyt 4, čep hlavního úchytu 1 |
| Podložka M3 (DIN 125) | 12 | pod matice |
| Pružná podložka M3 | 2 | hlavní pant – nastavení tuhosti |
| Ocelový kolík 3 × 14 mm (ISO 2338) | 2 | šoupátka |
| Ocelový drát nebo tyčinka Ø 2 mm, 80 mm | 2 | čepy pantů dvířek |
| Samořezný šroub do plastu M3×10 | 4 | přítlačné lišty displeje |
| Samořezné šrouby do plastu M3 | podle potřeby | součástky na mřížku na víku |
| Klíčenka (šňůrka s kovovou karabinkou) | 3 | 1 od krku k úchytu 15, 2 z podpaží k 13 a 14 |

Doporučuji nerezové šrouby a kolíky.

Nářadí: imbus 2,5 mm (DIN 912) a 2 mm (ISO 7380), páječka s nástavcem na zalisovací matice (245–260 °C), klíč 5,5 mm, kleště na stříhání drátu.

## 3. Montáž

1. **Zalisovací matice:** zalisuj je páječkou na 245–260 °C, kolmo a bez tlaku, ať zapadnou samy. Patří do pravé poloviny těla (spojovací žebra), do sloupků v rozích a v žebrech pro víko, do zesílení za čelem pro rámeček (zepředu), do bočních sloupků pro úchyty a do sloupků pro opěrku. Levá polovina stejně, jen bez 4 matic ve spojovacích žebrech.
2. **Spoj polovin:** přilož obě poloviny těla k sobě a sešroubuj je 4 šrouby M3×8 přes spojovací žebra, 2 nahoře a 2 dole. Šrouby jdou z levé poloviny a utahuje se imbusem zevnitř.
3. **Displej:** vlož displej zevnitř sklem do okna. Lišty 7 a 8 přišroubuj samořeznými šrouby do sloupků, přitlačí horní a dolní okraj displeje.
4. **Dvířka:** nasaď dvířka na panty rámečku a protlač drát Ø 2 mm. V rámečku drží drát napevno, v dvířkách má vůli.
5. **Rámeček:** přišroubuj ho zepředu 8 šrouby ISO 7380. Rámeček je jeden kus přes obě poloviny, takže spoj ještě zpevní zepředu. Přes rámeček a čelo prostrč a přitáhni matice páčkových přepínačů.
6. **Deska stínítka:** vlož ramena desky mezi uši rámečku a spoj je šroubem M3×20 s podložkami, pružnou podložkou a pojistnou maticí. Matici dotáhni tak, aby deska držela v libovolné poloze.
7. **Šoupátka:** vtlač ocelový kolík do knoflíku a knoflík zasuň do vodítka na desce.
8. **Hlavní úchyt:** úchyt 15 přišroubuj pod displej 4 šrouby M3×16 skrz úchyt, rámeček a čelo, zevnitř s podložkou a pojistnou maticí. Úchyt je vidlice otevřená k tobě: šroub M3×25 prostrč napříč oběma oky a zajisti pojistnou maticí. To je čep pro karabinku.
9. **Boční úchyty:** úchyty 13 a 14 přišroubuj každý 3 šrouby M3×20 do matic ve stěně. Horní šroub je zároveň čep: vede vodorovně ze stěny ven a úchyt je nad ním a před ním otevřený.
10. **Opěrka:** přišroubuj TPU opěrku 16 na spodní hranu 2 šrouby M3×8.
11. **Elektronika a víko:** namontuj součástky na mřížku sloupků na víku (samořezné šrouby M3, kabely stáhni páskami přes očka). Poloviny víka přišroubuj zezadu 8 šrouby M3×8.

## 4. Klíčenky

Karabinka klíčenky se cvakne kolem ocelového šroubu (čepu). Čep je vždy kolmo na směr tahu a úchyt je otevřený tam, kam šňůrka vede, takže se karabinka natočí za šňůrkou a nikde se neopírá o hranu. Drží za ocel, ne za plast. Hlavní šňůrka vede od krku po těle k úchytu 15 pod displejem a nese většinu váhy. Dvě boční šňůrky přivaž u krku liščím uzlem na hlavní a veď je podpažím k úchytům 13 a 14. Ovladač se spodní hranou s TPU opěrkou opírá o břicho.

## 5. Používání stínítka

1. Zvedni desku nahoru.
2. Otevři dvířka do pravého úhlu.
3. Polož desku na dvířka, jazýčky zapadnou do drážek.
4. Zasuň šoupátka. Stínítko je pak zajištěné proti větru.

Při převozu jsou dvířka zaklapnutá přes displej a navrchu leží deska, kterou drží tření v hlavním pantu.

## 6. Co je potřeba ověřit

Gimbaly, páčkové přepínače a elektronika v modelu nejsou, protože neznám jejich přesné rozměry. Před tiskem velkých dílů ověř hlavně tyto věci:
- **Gimbaly:** uvnitř u horních rohů jsou zesílení pro boční úchyty (8 mm od boční stěny, 45–60 mm nad středem, od čela až 6 mm od zadní stěny). Tělo gimbalu do nich nesmí zasahovat.
- **Palce:** otevřená dvířka stojí asi 30 mm od středu gimbalů. Ověř, že o ně palec nezavadí při plné výchylce páky.
- **Páčkové přepínače:** zavřená i otevřená deska stínítka je pod nimi, ověř výšku páček.
- **Displej:** sloupky pro lišty počítají s displejem tlustým 7 mm (sklo a panel). Pokud je tvůj tlustší, napiš mi a sloupky upravím.
- **Otvory:** všechny otvory z původního návrhu (displej, gimbaly, přepínače, kolébkové spínače, antény, posuvník) mají stejné rozměry a polohy jako ve tvém původním modelu.
