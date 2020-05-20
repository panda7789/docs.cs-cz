---
title: Vzory pozorovatelnosti
description: Vzory pozorování pro cloudové nativní aplikace
ms.date: 05/13/2020
ms.openlocfilehash: db6a56358923025cbcca9478908474227e5da96d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613808"
---
# <a name="observability-patterns"></a>Vzory pozorovatelnosti

Stejně jako byly vyvinuty vzory pro podporu v rozložení kódu v aplikacích, existují vzory pro operační aplikace spolehlivě. Existují tři užitečné vzory pro údržbu aplikací: **protokolování**, **monitorování**a **výstrahy**.

## <a name="when-to-use-logging"></a>Kdy použít protokolování

Bez ohledu na to, jak opatrní, se aplikace téměř vždy chovají neočekávaným způsobem v produkčním prostředí. Když uživatelé nahlásí problémy s aplikací, je velmi užitečné, abyste mohli zjistit, co se v aplikaci v případě problému stalo. Jedním z nejpravděpodobnějších a pravdivých způsobů, jak zachytit informace o tom, co aplikace provádí během chodu, je nechat aplikaci zapisovat, co dělá. Tento proces se označuje jako protokolování. V době, kdy dojde k selhání nebo k problémům v produkčním prostředí, by měl být cílem reprodukce podmínek, za kterých došlo k selhání, v neprodukčním prostředí. Po vhodném přihlášení poskytuje vývojářům plán, jak postupovat v prostředí, které lze testovat a experimentovat s.

### <a name="challenges-when-logging-with-cloud-native-applications"></a>Problémy při protokolování s využitím nativních aplikací cloudu

V tradičních aplikacích se soubory protokolu obvykle ukládají na místním počítači. Ve skutečnosti v operačních systémech, které používají systém UNIX, je definována struktura složek, která bude obsahovat všechny protokoly, obvykle v části `/var/log` .

![Protokolování do souboru v aplikaci ](./media/single-monolith-logging.png)
 monolitické **Obrázek 7-1**. Protokolování do souboru v aplikaci monolitické

Užitečnost protokolování do plochého souboru na jednom počítači se výrazně snižuje v cloudovém prostředí. Aplikace vytvářející protokoly nemusí mít přístup k místnímu disku nebo je místní disk vysoce přechodný, protože kontejnery jsou v rámci fyzických počítačů přemísťování. I jednoduché škálování aplikací monolitické napříč více uzly může zjednodušit vyhledání příslušného souboru protokolu založeného na souborech.

![Protokolování do souborů v aplikaci monolitické s měřítkem. ](./media/multiple-node-monolith-logging.png)
 **Obrázek 7-2**. Protokolování do souborů v aplikaci monolitické s měřítkem.

Nativní aplikace v cloudu vyvinuté pomocí architektury mikroslužeb také představují problémy pro protokolovací soubory založené na souborech. Žádosti uživatelů teď můžou zahrnovat několik služeb, které běží na různých počítačích a můžou zahrnovat funkce bez serveru bez přístupu k místnímu systému souborů. V rámci těchto mnoha služeb a počítačů by bylo velmi náročné korelovat protokoly od uživatele nebo relace.

![Protokolování do místních souborů v aplikaci mikroslužeb. ](./media/local-log-file-per-service.png)
 **Obrázek 7-3**. Protokolování do místních souborů v aplikaci mikroslužeb.

Nakonec je velký počet uživatelů v některých aplikacích nativních pro Cloud. Představte si, že každý uživatel při přihlášení k aplikaci vygeneruje stovky řádků protokolu. V izolaci, která je spravovatelná, ale vynásobte to více než 100 000 uživatelů a objem protokolů je dostatečně velký, aby byly k dispozici specializované nástroje pro podporu efektivního používání protokolů.

### <a name="logging-in-cloud-native-applications"></a>Protokolování v cloudových nativních aplikacích

U každého programovacího jazyka jsou k dispozici nástroje, které umožňují zápis protokolů, a obvykle jsou režie pro zápis těchto protokolů nízká. Mnohé z knihoven protokolování poskytují protokolování různých druhů závažnosti, které mohou být vyladěny v době běhu. Například [Knihovna Serilog](https://serilog.net/) je oblíbená strukturovaná knihovna protokolování pro .NET, která poskytuje následující úrovně protokolování:

* Verbose
* Ladit
* Informace
* Upozornění
* Chyba
* Závažná

Tyto různé úrovně protokolu poskytují v protokolování členitost. Když aplikace funguje v produkčním prostředí správně, může být nakonfigurována pouze k protokolování důležitých zpráv. Pokud se aplikace nechová, je možné zvýšit úroveň protokolu, aby se shromáždily podrobnější protokoly. To vyvažuje výkon proti snadnému ladění.

Vysoký výkon nástrojů protokolování a tunability podrobností by měl vývojářům přizvat k častému protokolování. Řada upřednostňuje vzor protokolování vstupu a ukončení jednotlivých metod. Tento přístup může být podobný jako přehnaně důkladné, ale je nečastější, že vývojáři budou chtít snížit protokolování. Ve skutečnosti není Neběžné provádět nasazení pouze pro účely přidávání protokolování do problematické metody. Chyba na straně příliš velkého množství protokolování a není příliš malá. Některé nástroje lze použít k automatickému poskytnutí tohoto typu protokolování.

Z důvodu problémů spojených s používáním protokolů založených na souborech v cloudových nativních aplikacích jsou upřednostňovány centralizované protokoly. Protokoly jsou shromažďovány aplikacemi a dodávány do centrální protokolovací aplikace, která indexuje a ukládá protokoly. Tato třída systému může každý den ingestovat desítky gigabajtů protokolů.

Při sestavování protokolování, které zahrnuje mnoho služeb, je také užitečné dodržovat některé standardní postupy. Například generování [ID korelace](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) na začátku zdlouhavé interakce a jejich protokolování v každé zprávě, která souvisí s touto interakcí, usnadňuje hledání všech souvisejících zpráv. Jedna zpráva potřebuje najít jenom jednu zprávu a extrahovat ID korelace a najít všechny související zprávy. Dalším příkladem je zajistěte, aby byl formát protokolu pro každou službu stejný, bez ohledu na to, jaký jazyk nebo knihovna protokolů používá. Díky této standardizaci je čtení protokolů mnohem jednodušší. Obrázek 7-4 ukazuje, jak může architektura mikroslužeb využít centralizované protokolování v rámci svého pracovního postupu.

![Protokoly z různých zdrojů se ingestují do centralizovaného úložiště protokolů. ](./media/centralized-logging.png)
 **Obrázek 7-4**. Protokoly z různých zdrojů se ingestují do centralizovaného úložiště protokolů.

## <a name="challenges-with-detecting-and-responding-to-potential-app-health-issues"></a>Výzvy k detekci a reakci na potenciální problémy s kompatibilitou stavu aplikací

Některé aplikace nejsou klíčové. Je možné, že se používají jenom interně, a když dojde k problému, může uživatel kontaktovat odpovědného týmu a aplikace se může restartovat. Zákazníci ale mají často větší očekávání pro aplikace, které spotřebovávají. Měli byste vědět, kdy k problémům dochází ve vaší aplikaci *předtím, než* se uživatelé dostanou. V opačném případě se může stát, že když si všimnete, že Angry Deluge příspěvky sociálních médií do vaší aplikace nebo dokonce vaší organizace, může to být první, co víte o problému.

Mezi scénáře, které možná budete potřebovat vzít v úvahu, patří:

- Jedna služba ve vaší aplikaci zajišťuje neúspěšné a restartování, což vede k občasné pomalé odezvy.
- Čas odezvy vaší aplikace je v určitou dobu pomalý.
- Po nedávném nasazení je zatížení databáze trojnásobné.

Při správné implementaci vám monitorování může informovat o podmínkách, které vedou k problémům, a zajistit tak splnění základních podmínek, které budou mít za následek značný dopad na uživatele.

### <a name="monitoring-cloud-native-apps"></a>Monitorování nativních aplikací v cloudu

Některé centralizované systémy protokolování přijímají další roli shromažďování telemetrie mimo čistých protokolů. Můžou shromažďovat metriky, jako je čas pro spuštění databázového dotazu, Průměrná doba odezvy z webového serveru a dokonce i průměr zatížení procesoru a tlak na paměť, který je hlášený operačním systémem. V kombinaci s protokoly můžou tyto systémy poskytovat holistický zobrazení stavu uzlů v systému a aplikace jako celku.

Funkce shromažďování metriky, které jsou v rámci aplikace pro monitorování metriky, je také možné v aplikaci ručně doplňovat. Obchodní toky, které mají zvláštní význam, jako jsou například noví uživatelé registrace nebo objednávky, mohou být instrumentované tak, že zvýší čítač v centrálním monitorovacím systému. To odemkne nástroje pro monitorování, aby nesledovaly jenom stav aplikace, ale i stav podniku.

Dotazy se dají vytvořit v nástrojích pro agregaci protokolů a vyhledat konkrétní statistiky nebo vzory, které se pak dají zobrazit v grafickém formuláři, na vlastních řídicích panelech. Týmy budou často investovat do rozsáhlých displejů připojených k stěnám, které se pohybují prostřednictvím statistik vztahujících se k aplikaci. Tímto způsobem je snadné zobrazit problémy tak, jak se vyskytují.

Nástroje pro monitorování nativní pro Cloud poskytují telemetrie v reálném čase a nabízí přehled o aplikacích bez ohledu na to, jestli jsou monolitické aplikace s jedním procesem nebo distribuované architektury mikroslužeb. Zahrnují nástroje, které umožňují shromažďování dat z aplikace a také nástroje pro dotazování a zobrazování informací o stavu aplikace.

## <a name="challenges-with-reacting-to-critical-problems-in-cloud-native-apps"></a>Problémy s tím, jak reagovat na kritické problémy v cloudových nativních aplikacích

Pokud potřebujete reagovat na problémy s vaší aplikací, budete potřebovat nějaký způsob, jak upozornit na správné pracovníky. Toto je třetí model závislosti aplikace v nativním cloudu a závisí na protokolování a monitorování. Vaše aplikace musí mít místo přihlášení, aby bylo možné diagnostikovat problémy, a v některých případech předávat do monitorovacích nástrojů. Potřebuje monitorovat agregované metriky aplikací a data o stavu na jednom místě. Jakmile je tato operace navázána, je možné vytvořit pravidla, která aktivují výstrahy, když určité metriky přestanou být mimo přijatelné úrovně.

Obecně platí, že výstrahy jsou vrstveny nad monitorováním, aby určité podmínky aktivovaly příslušné výstrahy, aby upozornily členy týmu na naléhavé problémy. Mezi scénáře, které mohou vyžadovat výstrahy, patří:

- Jedna ze služeb vaší aplikace po 1 minutách výpadků nereaguje.
- Vaše aplikace vrací neúspěšné odpovědi HTTP na více než 1% požadavků.
- Průměrná doba odezvy vaší aplikace pro klíčové body překračuje 2000 MS.

### <a name="alerts-in-cloud-native-apps"></a>Výstrahy v cloudových nativních aplikacích

Můžete vytvářet dotazy na nástroje pro monitorování a hledat tak známé stavy selhání. Dotazy například můžou vyhledat přes příchozí protokoly pro indikaci stavového kódu HTTP 500, což indikuje problém na webovém serveru. Jakmile se zjistí jedna z těchto hodnot, může se e-mailem nebo serverem SMS odeslat vlastníkovi původní služby, která může začít prozkoumat.

Obvykle ale jedna chyba 500 není dostačující k určení toho, že došlo k problému. Může to znamenat, že uživatel nesprávně zadal svoje heslo, nebo zadal některá poškozená data. Dotazy na upozornění se dají vytvořit tak, aby se aktivovaly jenom v případě, že se zjistí větší než průměrný počet chyb 500.

Jedním z nejvíce škodlivých vzorů při upozorňování je vyvolat příliš mnoho výstrah, aby se lidé mohli prozkoumat. Vlastníci služby se rychle odeberou na chyby, které byly dříve prověřené a které byly shledány neškodně. Když dojde k skutečným chybám, ztratí se v důsledku výskytu stovky falešně pozitivních hodnot. Parable pro [Boy, kteří provedli Jillian,](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) se často dozvěděli dětem, aby jim upozornili na toto velmi nebezpečné. Je důležité zajistit, aby výstrahy, které se aktivují, byly indikativní pro skutečný problém.

>[!div class="step-by-step"]
>[Předchozí](monitoring-health.md) 
> [Další](logging-with-elastic-stack.md)
