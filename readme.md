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
      > **Modulární PLC** => složení CPU a samostatných externích modulů pro rozšíření/přidání nových fcí.
      >                   - škálování dle potřeby, hl. pro komplexní systémy,
      >                   - výrobní linky, hotely, distr. zař.
      > **BMS**v => centrální sys., který řídí a monitoruje technologie v budově
      >             - např.: světla, vytápění, ventilace, zabezpečené, přístupové systémy, energ. management
      >    -> pro fci se musí použít **standardizované protokoly**
      >       1) **BACnet** -> pro HVAC, osvětlení, senzory, měření energie
      >                   - otevřený protokol, velká podpora (siemens, honeywell,...)
      >                   - hotely, velké budovy, nemocnice
      >       2) **KNX** -> domácí a budová automatizace (žaluzie, osvětlení, topení)
      >                   - evropský standard, rezidenční a komerční budovy
      >                   - smart home, kanceláře, školy
      >       3) **Modbus** -> průmyslevé aplikace, měření, řízení
      >                   - jednoduchý široce rozšiřitenlý, skrze RS485 nebo TCP/IP
      >                   - výrobní linky, kotelny, měření spotřeby

3. K nalezeným PLC dohledejte a vysvětlete následující parametry:
    - Parametry CPU
    - Velikosti a typy pamětí
    - Napájecí napětí a odběr (proud při napájecím napětí)
    - Modulární/kompaktní
    - Počty digitálních a analogových vstupů a výstupů a jejich využití
    - Další rozhraní pro komunikaci PLC s okolím (pro programování samotného PLC, tak i pro rozšíření o další moduly a zařízení)

4. V automatizační technice se setkáme s řadou dalších řídících jednotek. Zjistěte, jaké se označují následujícími zkratkami a pro jakou oblast automatizace se používají:
    - iPC
    - NC (Numerical Control)
    - MCU

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

2. Vymyslete postup, jak pomocí multimetru ověřit:
    - Napětí na napájecích svorkách zdroje a PLC, případně dalších komponent
    - Zkrat mezi vodiči
    - Prohození vodičů
    - Stav DO
    - Spečené reléové kontakty

<details>
    <summary> :bulb: Tip: </summary>
        Podívejte se na štítkové údaje, případně do technických listů. Naleznete v nich některé informace potřebné pro diagnostiku.
</details>

3. Diagnostiku PLC lze provádět i pomocí programovacího prostředí (IDE). K čemu slouží následující nástroje:
    - Forced value (vnucení/uzamknutí hodnot)
    - Nástroje Watch a Monitor
    - Debugger
    - Log soubory
    - ...

<details>
    <summary> :bulb: Tip: </summary>
        Otevřete si programovací prostředí pro PLC a uvedené nástroje vyhledejte a vyzkoušejte. Je možné, že v některých prostředích některé nástroje nenaleznete, nebo pod jiným názvem (poznamenejte si tyto názvy). Případně zkuste zjistit jiné diagnostické nástroje.
</details>

### 4. Programovací jazyky pro PLC

1. Založte projekt a v něm programy v pěti jazycích (ST - Struktural Text, LD - Ladder Diagram, CFC - Continous Function Chart a dvou dalších podle vlastního výběru).

2. V každém jazyce napište a odzkoušejte program pro zpožděné vypnutí světla.

> :key: **Programovací jazyky pro PLC**
>
> Programovacími jazyky pro PLC se zabývá norma IEC 61 131-3. 


