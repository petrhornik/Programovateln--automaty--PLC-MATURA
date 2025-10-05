[Co dodělat ]: #
[nic ]: #

# Programovatelné automaty (PLC)

$${\color{#FFA500}BUDE U MATURITY }$$

## Cíl
-   Studenti se budou orientovat v běžných PLC a rozliší je podle primárního využití.
-   Budou mít povědomí o dalších řídících jednotkách, používaných v automatizaci.
-   Popíší základní části PLC,
-   a provedou základní diagnostiku.
-   Dále se studenti budou orientovat v oblasti programovacích jazyků pro PLC.

## Ověření cílů

Programovatelné automaty (PLC)

1) Základní vlastnosti, rozdělení: podle použití, velikosti a podle modulárnosti
2) Popis částí PLC
3) Základní diagnostika PLC
4) Programovací prostředí a programovací jazyky pro PLC

## Úlohy

### 1. Základní vlastnosti a rozdělení PLC

> PLC = řidící jednotka používaná v průmyslu a automatizaci budov

> :key: **PLC**
>
> Programovatelný logický automat
> Programovatelný logický automat. Online. In: Wikipedia: the free encyclopedia. San Francisco (CA): Wikimedia Foundation, 2024, 23. 2. 2024 v 09:19. Dostupné z: https://cs.wikipedia.org/wiki/Programovateln%C3%BD_logick%C3%BD_automat. [cit. 2024-12-28].

1. Jaký je rozdíl mezi PLC a embedded PLC? Co znamená slovo embedded obecně a u jakých dalších typů řídících jednotek se používá?
   >
   > klasické PLC
   >  - samostatné větší zařízení co se montuje samostatně
   >  - jednodušší přístup a opravy
   >  - je modulární dá se upravovat
   >  - jednodušší nasazení - propojuje se se zbytkem HW externě dráty
   >  - robustnější konstrukce s lepší výdrží pro průmyslové nasazení
   
   > Embedded => označuje že je komponenta či souřástka je napevno umístěna např.: k PCB
   >             - např. kontroler integrovaný obvobu
   
   > Embedded PLC
   >  - celý systém navržen jako 1 PCB - veškeré komponenty integrovány
   >  - levnější na výrobu - vše na 1 desce = jednotná výroba
   >  - kompaktní - nezabere tolik místa
   >  - hl. v DIY, IoT, řízení s vizualizací
   > 
> PLC se často rozdělují podle výkonu, ale lepší je rozlišovat pro jakou oblast automatizace jsou určena.

2. Vyhledejte a zdůvodněte konkrétní typy PLC pro následující oblasti použití:
    - Automatizace rodinných domů a bytů
      >
      > Použít kompaktní či embedded PLC - např. jednodušší Siemens, LOGO!, Fatek
      > - není potřeba vel. množ. inputů/outputů
      > - Jednoduché na nastavení/programování
      > - integrovaný "centrální" ovládací panel či webové GUI
      > - např. světla, žaluzie, topení, závlahy, ...
      > - **Výhody** nízká cena, snadná integrace např. do rozvaděče
      > - embedded v případě, že mám nějaké zař. s integrovaným PLC co slouží např. jako wireless hub
    - Automatizace jednoúčelových strojů
      >
      > Použít modulární PLC - např. Siements S7-1200, Mitsubishi FX5U - možná by šlo i kompaktní pro jednodušší účely
      > - potřeba vyššího výkonu než u domácích
      > - možnost rozšíření o analogové I/O a další komunikační moduly
      > - je potřeba rychlejší odezvy pro řízení motorů, senzorů, pneumatických prvků,...
      > - **Výhody** flexibilita a spolehlivost pro specifické úlohy
    - Automatizace hotelů a větších budov občanské výstavby
      >
      > Použít modulární PLC umožňující vzdálenou správu - např.: Wago 750, Beckhoff CX
      > - je potřeba řídit několik zón (přístupový sys., světla, klimatizace, ...)
      > - hodí se podpora BACnet, KNX, Modbus pro integraci s BMS (Building Management System)
      > - správa na dálku bez fyz. přístupu je vyžadována (hotelové komplexy mají více než 1 budovu) + ušetří čas
      > - **Výhoda** ->škálovatelnost a kompatibilita se systémy budovy
    - Automatizace výrobních linek
      >
      > Modulární PLC s vysokým výkonem - např.: Siemens S7-1500, Allen-Bradley CompactLogix
      > - je potřeba řízení nekolika stanic, robotů, dopravníků najednou
      > - nutná podpora real-time komunikace (Profined, EtherCAT)
      > - hodí se možnost připojení bezpečnostích modulů (pro detekci nebezpečí na lince - security(aktivní prvek))
      > - **Výhoda** -> rychlé zpracování dat, robustní konstrukce, pokročilé diagnostické fce.
    - Automatizace velkých továren, elektráren, apod.
      >
      > Použít pravděpodobně rackové PLC nebo PAC (programovatelný auto. kontroler)
      > - např.: Siements S7-400, cokolo od Schneider Electronics
      > - Nutnost velkého množství I/O a redundantní CPU
      > - podpora DCS (distribuční řídící systém)
      > - odolnost vůči extrémním podmínkám - hl. vysoké teploty a vibrace
      > - **Výhoda** -> maximální spolehlivost, dlouhá životnost, možnost zálohování a vzdálené správy(remote)
    - NAVÍC
      > **Kompaktní PLC** => vše integrováno v 1 CPU a nelze rozšířit o další moduly
      >                - pevně daný počet I/O, jednoduché nasazení, nízká cena
      >                - hl. v malých automatizacích (domovy, jednouč. stroje)
      >
      > **Modulární PLC** => složení CPU a samostatných externích modulů pro rozšíření/přidání nových fcí.
      >                   - škálování dle potřeby, hl. pro komplexní systémy,
      >                   - výrobní linky, hotely, distr. zař.
      
      > **BMS**v => centrální sys., který řídí a monitoruje technologie v budově
      >             - např.: světla, vytápění, ventilace, zabezpečené, přístupové systémy, energ. management
      >    -> pro fci se musí použít **standardizované protokoly**
      >
      >       1) **BACnet** -> pro HVAC, osvětlení, senzory, měření energie
      >                   - otevřený protokol, velká podpora (siemens, honeywell,...)
      >                   - hotely, velké budovy, nemocnice
      >       
      >      2) **KNX** -> domácí a budová automatizace (žaluzie, osvětlení, topení)
      >                   - evropský standard, rezidenční a komerční budovy
      >                   - smart home, kanceláře, školy
      >
      >       3) **Modbus** -> průmyslevé aplikace, měření, řízení
      >                   - jednoduchý široce rozšiřitenlý, skrze RS485 nebo TCP/IP
      >                   - výrobní linky, kotelny, měření spotřeby

3. K nalezeným PLC dohledejte a vysvětlete následující parametry:
    - Parametry CPU -> hlavní řídící jednotka
      > - **Frekvence** => rychlost zprac. instrukcí (100 MHz, 1GHz)
      > - **Počet jader** => čít víc jader, tím víc addidas
      > - **Typ CPU uvnitř CPU** => CISC nebo RISC
    - Velikosti a typy pamětí
      > **Programová** => zde je kód, omezení komplexnosti dle velikosti, uchovává data po vypnutí
      >                - low-end: 2-128KB, mid-end: 128-512KB, mid+-end: 1-8MB, high-end: 8-32MB
      
      > **Datová(RAM)** => proměnné, stavy, běžící procesy, aktuální data, NEuchovává data po vyp.
      >                - low-end: 1-64KB, mid-end: 64-256KB, mid+-end: 1-4MB, high-end: 4-16MB
      
      >  **Externí** => SD karta nebo USB pro zálohy, logování pro diagnostiku, ...
      >                - - low-end: volitelné, mid-end: cca 2GB, mid+-end: 32GB SD/CF, high-end: redundantní paměť. moduly
    - Napájecí napětí a odběr (proud při napájecím napětí)
      > **napětí** => nejčastější varianty
      >    1) **DC** -> 24V stejnosměr., hl. v průmyslu, bezpečné, kompatibilní s většinou senzorů
      >    2) **AC** -> 100-240V střídavé, u některých kompaktních PLC (siemens, LOGO!)
      >    3) **Nízké DC** -> 12V stejnosměr., u embedded PLC a DIY (RPI PI + Codesys)

      > **odběr** => spotřeba proudu při daném napájecím napětí PLC
      >          - zavisí na: typ CPU, počet připojených I/O modulů, připojené periferie
      >          - např.:
      >
      > <img src="Snímek obrazovky 2025-09-29 211140.png">
    - Modulární/kompaktní
      > vše je v sekci NAVÍC !
    - Počty digitálních a analogových vstupů a výstupů a jejich využití
      > - **Digi vst(DI)** -> Tlačítka, senzory – 0/1 logika.
      > - **Digi výst(DO)** -> Relé, LED, elektromagnety – zapnout/vypnout.
      > - **Analog vst(AI)** -> Teplota, tlak, hladina – např. 0–10 V, 4–20 mA.
      > - **Analog výst(AO)** -> Řízení motorů, ventilů – plynulé signály.
      > - **Využití** -> DI/DO pro logiku, AI/AO pro regulaci a měření.

    - Další rozhraní pro komunikaci PLC s okolím (pro programování samotného PLC, tak i pro rozšíření o další moduly a zařízení)

4. V automatizační technice se setkáme s řadou dalších řídících jednotek. Zjistěte, jaké se označují následujícími zkratkami a pro jakou oblast automatizace se používají:
    - iPC
      > => industrial PC (průmyslový osobní počítač) - slouží jako regulátor ve strojním zařízení
      > - odolnost proti prachu, provoz 24/7, možnost montáže např. do rozvaděče, fanless
      > - řízení výrobních procesů, zobraz. HMI (human machine interface), běh SCADA systémů, integ. s cloudem
    - NC (Numerical Control)
      > => číslicové zařízení - automatizace obráběcích a dalších storjů ovládaných ručně přes kola a páky či jakákoli mechanická automatizace
      > - automatizace CNC (computer numerical controlled) strojů, automatizace manuálních strojů
    - MCU
      > => micro-controller unit (jednočip) - rpi pi pico, esp32, jakýkoli integrovaný obvod obsahující mikropočítač
      > - v embedded systémech, v mobilech, domácí spotřebiče, bezpečnostní systémy, ...

### 2. Části PLC

1. U zvoleného výrobce vyhledejte v katalogu, případně e-shopu, či konfigurátoru, jednotlivé komponenty pro funkční sestavu PLC s následujícími parametry:
    - CPU 32b nebo vyšší
    - 23 DI
    - 7 AI
    - 4 DO s PWM
    - 2 DO
    - 3 reléové výstupy
    - Sběrnice s možností rozšíření o vzdálené moduly IO

<details>
    <summary> :bulb: Tip: </summary>
        Některé firmy vyrábějící modulární PLC používají tzv. konfigurátory sestav, které bývají součástí IDE a případně propojeny s e-shopem.
        Další možností, jak si usnadnit práci, je zaslat požadavek přímo firmám jako předběžnou poptávku. Získáte tak i informaci o cenách.
</details>

> :key: **CPU u PLC**
>
> Ačkoliv zkratka CPU je obecně brána jako označení mikroprocesoru, u PLC se tím obvykle myslí celý řídící modul, který v dnešní době může obsahovat více procesorů.

2. Podrobněji prozkoumejte parametry CPU 

3. Zjistěte nejen typ sběrnice, ale i její hlavní parametry. Můžete zkusit zjistit i informace o použitém protokolu.

### 3. Základní diagnostika PLC

1. Vyhledejte technický list vybraného PLC a zjistěte, co lze zjistit o PLC z kontrolek (LED na samotném PLC).
   > => stav vstupů, stav připojení antény, sygnalizace běhu, chyby, připojeného USB, display pro další info
   <img width="682" height="440" alt="Snímek obrazovky 2025-10-05 204439" src="https://github.com/user-attachments/assets/bed234d5-0e21-4c5a-acf3-c9d319fc5ee7" />


2. Vymyslete postup, jak pomocí multimetru ověřit:
    - Napětí na napájecích svorkách zdroje a PLC, případně dalších komponent
      > 1) nastavím multimetr na stejnosměr. V
      > 2) černej dám na GND a červenej na 24V (napájení input)
      > 3) proměřím takto: PLC, I/O moduly, senzory, ...
    - Zkrat mezi vodiči
      > 1) Vypnu napájení a koncovku si dám na VIDITELNÉ místo
      > 2) multimetr na pípák (dioda)
      > 3) změřím co jde mezi výstupy, vstupy, jednot. vodiči
      > 4) pípnutí = spojení (možný zkrat)
    - Prohození vodičů
      > 1) ověřit si správnost zapojení dle schématu
      > 2) pomocí pípáku změřit konce konkrétního vodíče
      > 3) pípnutí = ten samý vodič (nebo zkrat)
    - Stav DO
      > 1) zapnu do sítě a přes HMI/ručně přepnu DO výstup
      > 2) multimetr na stenjosměr V
      > 3) měřit mezu DO a GND, zap. výstup -> 24V, vypnutý -> 0V
    - Spečené reléové kontakty
      > 1) vypnout napájení
      > 2) odpojit výstupní svorky relé (NO/NC kontakt)
      > 3) multimetr na test obporu
      > 4) změřit NO a COM -> při vypnutí musí být rozepnuté
      > 5) NC a COM -> musí být rozepnuté

<details>
    <summary> :bulb: Tip: </summary>
        Podívejte se na štítkové údaje, případně do technických listů. Naleznete v nich některé informace potřebné pro diagnostiku.
</details>

3. Diagnostiku PLC lze provádět i pomocí programovacího prostředí (IDE). K čemu slouží následující nástroje:
    - Forced value (vnucení/uzamknutí hodnot)
      > => lze ručně nastavit hodnotu proměnné - hl. pro ladění, testování či simulaci
      > - např. simulace aktivního sensoru, chci vědět jak se prog. zachová při zapnutém sensoru tak dočasně nastavím jeho prom. na forced ON
      > - přepisuje běžnou logiku, vše je potřebo na konci vrátit manuálně do původního stavu
    - Nástroje Watch a Monitor
      > => lze sledovat hodnoty proměnných v reálném čase za běhu prog.
      > - watchlist => seznam prom., které si ručně vyberu a sleduu jejich akt. hodnoty
      > - monitor mode => zobrazení hodnot přímo v kódu, u jednot. příkazů, hl. v ladderu nebo STL/FBD
    - Debugger
      > => pokročilé ladění prog. step-by-step - lze zastavit prog. v urč. místě pro analýzu stavu za urč. podmínek
      > - Breakpoints => zastaví prog. na urč. řádku
      > - call stack => sleduje vnořené volání fcí/FB
    - Log soubory
      > => záznamy událostí, chyb, warningů, hodnot a prom. in real time
      > - zpětná alalýza závad nebo nestandardního chování
      > - error logs => chyby co nastaly při běhu
      > - historie změn prom. => datalogging (grrafy, trendování)
      > - sys. logy IDE => sestavení projektu, připojení k POLC, překlad chyb 
    - ...

<details>
    <summary> :bulb: Tip: </summary>
        Otevřete si programovací prostředí pro PLC a uvedené nástroje vyhledejte a vyzkoušejte. Je možné, že v některých prostředích některé nástroje nenaleznete, nebo pod jiným názvem (poznamenejte si tyto názvy). Případně zkuste zjistit jiné diagnostické nástroje.
</details>

### 4. Programovací jazyky pro PLC

1. Založte projekt a v něm programy v pěti jazycích (ST - Struktural Text, LD - Ladder Diagram, CFC - Continous Function Chart a dvou dalších podle vlastního výběru).
> 1) LD (LAD) => grafický jaz. (vypadá jako tech. schéma), snadno čitelný
>             - využití pro log. operace, spínáíní, řízení výstupů
>             - zákl. prvky: kontakty (NC, NO), cívky, časovače, počítadla
>
> 2) FBD (funciton block diagram) => blokové schéma, fce. zapojené jako krabičky s I/O, dobré pro řízení analog. signálů, PID regulace,...
>                                 - hl. pro strukturované a opakující se fce.
>
> 3) ST => textový jaz. podobný C, Pascal - pro složitější výpočty, podmínky, cykly, prácí s daty
>       - efektivní a přehledné, nejpoužívanější
>
> 4) SFC (sequential function chart) => pro sekvenční řízení (sekce výroby, ...)
>                                    - prog. rozdělen na "kroky" a přechody - dobré pro stavové automaty, dávkový provoz, výrob. linky
>
> 5) CFC => neoficiální rozšíření IEC 61131-3, často používané (siemens, beckhoff)
>        - volné umisťování bloků do prostoru, paralelní a zpětné vazby, propojení libovolně čarami, reálné dat. toky
2. V každém jazyce napište a odzkoušejte program pro zpožděné vypnutí světla.

> :key: **Programovací jazyky pro PLC**
>
> Programovacími jazyky pro PLC se zabývá norma IEC 61 131-3. 


