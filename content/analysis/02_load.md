---
Title: Load Time
Description: This is my report page.
Template: analysis
---

# Load Time


I denna uppgift ingår att undersöka hur tre webbsidor fungerar gällande svarstider, dvs hur lång tid det tar att ladda upp en sida med allt innehåll.

# Urval
-----------------------

Jag har valt att titta på följande 3 företag
1.	ica
2.	xiaomi
3.	boozt

Denna gång har valt 3 företag utifrån shopping och intresse. Ica har jag sedan gammalt alltid använt som testsida för att kontrollera att nätet fungerar. Arbetade tidigare på företaget och medverkade i att ta fram en shopping-plattform.Därav lite extra kul att följa utvecklingen där. Xiamoi väljer jag delvis slumpmässigt och stötte på sidan när jag tittade efter en scooter. Tredje valet, boozt är den shop jag handlar på oftast och då blir det lite extra spännande att se hur denna står sig mot andra sidor. Summa summarum väljer jag detaljhandel och förhoppningsvis blir detta en bra jämförelse mellan företag inom samma bransch.









Metod
-----------------------

För de olika webbplatserna valde jag deras respektive startsida. Två av tre företag som 
finns tillgänglig för olika länder med ett av mitt val (ICA) riktar sig mot kunder i Sverige. Detta gör att de inernationella har olika suffix där det blir lätt att blanda mellan .com och .com/se. Jag fokuserade på startsidorna  och använde mig av google page speed som utför själva analysen och poängsätter utifrån olika kriterier.
Samtliga data finns insamlade i google spreadsheet, se refeerenser nedan.
Jag har testat och dokumenterat utfallet tre gånger för respektive företag.
När jag mätte prestanda via tools/network provade jag från olika browsers. Chrome fungerar dessvärre inte på min mac men jag provkörde den på en på en annan dator och gillar det jag ser. Där framhävs styrkan i att använda Google verktyg hela vägen ut. Jag gillar det inte men ser tendensen bland alla olika leverantörer. Eftersom jag är en mac användare testade jag istället Safari och Firefox. Efter en massa tvekan föll valet på firefox. 


Resultat
-----------------------

Nedan sammanfattas resultaten för de sidor jag testat och analyserat

## ica ##

![ica](../assets/img/ica.png)

### Sida 1 - Startsida
* Google PageSpeedInsights
    - Desktop: 54 poäng
    - Mobil: 7 poäng
* Snitt devtools (nätverk)
    - Laddtid: 11,06 s
    - Resurser: 101
    - Överförd storlek: 5,6 MB
    

## mi ##
![xiaomi](../assets/img/xiaomi.png)

* Google PageSpeedInsights
    - Desktop: 94 poäng
    - Mobil: 54 poäng
* Snitt devtools (nätverk)
    - Laddtid: 5,74 s
    - Resurser: 46
    - Överförd storlek: 5,89 MB
  
## boozt ##
![boozt](../assets/img/boozt.png)

* Google PageSpeedInsights
    - Desktop: 93 poäng
    - Mobil: 46 poäng
* Snitt devtools (nätverk)
    - Laddtid: 9,75 s
    - Resurser: 110
    - Överförd storlek: 9,75 MB

### Poängsammanställning PageSpeedInsights

![speed](../assets/img/pagespeed.png)

|  | ica | mi | boozt
:----- | :----: | -----: | -----:
desktop   | 54 | 94 | 93
mobile  | 7  | 54| 46

I desktopmätningen delar mi och boozt första plats där båda får mycket goda resultat. Ica hamnar klart sist med en hel del förbättringspotential. I mobilmätningen lyckas ingen nå toppresultat, mi är den som får godkänt men på marginalen medan både ica och boozt får underkänt. Ica får riktigt låga poäng med endast 7 poäng i mina mätningar.

### Poängsammanställning nätverk/devtools

|  | ica | mi | boozt
:----- | :----: | -----: | -----:
Laddtid   | 11,06 s | 5,74 s | 9,75 s
Resurser  | 101  | 46| 110
datamängd  | 5,6 MB  | 5,89 MB| 9,75 MB

mi ser ut att klara sig bäst här, halva laddtiden mot övriga men laddar också hälften så många resurser. Boozt sticker ut med störst laddad datamängd. I analysen nedan tar jag fram en tabell som visar varför Boozt blir vinnare i detta test.

Laddtiden för alla sidor är lång, jag skriver lite mera om detta i min analys. Det är samtidigt svårt att sätta just ett gränsvärde. I mina tester går jag just till startsidan och då kan jag acceptera längre svarstid för att sedan när jag klickar mig vidare får ett betydligt bättre resultat. Initiallt laddas ju mycket data som sedan finns cachat för nya sökningar. Spontant vill jag sätta ett gränsvärde på mindre än 2 sek men är tiderna jämnt fördelade kan det möjligen gå lite långsammare.

# Analys
-----------------------

Tabellerna nedan visar de mätresultat jag fått utifrån tre olika dimensioner. 
Largest Contentful Paint (LCP), mäter laddtiden. 
First Input Delay (FID): mäter interaktivitet.
Cumulative Layout Shift (CLS): mäter visuell stabilitet.  Utifrån olika riktvärden visas hur de olika webbsidorna lever upp till detta.

I min jämförelse har jag poängsatt varje förmåga där jag multiplicerat varje procent ett tal och sedan summerat samtliga mätningar för respektive bolag.
bra ger faktor 4, förbättringsbehov ger faktor 3.25 och dåligt ger 2.5.

## mätresultat desktop

![desktopdata3](../assets/img/desktopdata3.png)


Med en enkel räkneövning visar det sig att Boozt får högst poäng både för desktop som för mobil (se tabell nedan).
För att synliggöra resultatet och åskådligöra skillnaderna har jag färglagt till olika rutorna och förstärkt färgen där något sticker ut. Man ser då att det över lag ser ganska bra ut för boozt i de flesta mätningarna.

Nu skulle man kunna gå  vidare och se vad de olika värdena indikerar och antingen titta på det som är grön och see om det går att förstärka ytterligare. Kag väljer att titta på det rödmarkerade för att se vad som kan förbättras.

Jag upplever att alla sidor är hyfsat snabba men beaktar man laddtiderna så ger dessa alltför långa svarstider och det går att förbättra detta. I mitt fall rensar jag cachen något som såklart ger sämre prestanda. I verkliga livet kanske man accepterar detta, delvis då det är många bilder som ska laddas samtidigt som man får resultat medan laddning pågår.
På mi-sidan rekommenderas just att se över payload och Lighthouse flaggar om en request är större än 5000 KiB.

Generellt för sidorna kan följande beaktas för förättring:

* Oanvänd javascriptkod
* Fel format på bilder, användere bättre komprimering (next-gen format)
* Minska ner på js payload, mycket tid går till att parsa och evaluera js, html css osv.


## mätresultat mobil



![desktopdata3](../assets/img/mobiledata3.png)


    



# Referenser
-----------------------
[Google-Page-Speed-Desktop](https://docs.google.com/spreadsheets/d/1orbMpBRhi5lEYPRlL-UxvUaOkI5JZlGTwzanuuTy6VU/edit#gid=1673494939)

[Google-Page-Speed-Mobil](https://docs.google.com/spreadsheets/d/1orbMpBRhi5lEYPRlL-UxvUaOkI5JZlGTwzanuuTy6VU/edit#gid=1215494252)

[Network-rådata](https://docs.google.com/spreadsheets/d/1orbMpBRhi5lEYPRlL-UxvUaOkI5JZlGTwzanuuTy6VU/edit#gid=1676932147)


# Övrigt
-----------------------

Rapport framtagen av **Dan Erlandsson**


<div class="next-previous">
    <a href="01_colors"><i class="fas fa-chevron-left"></i></a>
    <a href="03_design-principles"><i class="fas fa-chevron-right"></i></a>
</div>
