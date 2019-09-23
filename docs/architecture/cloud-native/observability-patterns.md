---
title: Vzorce pro pozorování
description: Vzory pozorování pro cloudové nativní aplikace
ms.date: 09/23/2019
ms.openlocfilehash: 23320144c03278d631b8a1fcc1d1c0954e907296
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184874"
---
# <a name="observability-patterns"></a>Vzorce pro pozorování

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Stejně jako byly vyvinuty vzory pro podporu v rozložení kódu v aplikacích, existují vzory pro operační aplikace spolehlivě. Existují tři užitečné vzory pro údržbu aplikací: protokolování, monitorování a výstrahy.

## <a name="when-to-use-logging"></a>Kdy použít protokolování

Bez ohledu na to, jak opatrní, se aplikace téměř vždy chovají neočekávaným způsobem v produkčním prostředí. Když uživatelé nahlásí problémy s aplikací, je velmi užitečné, abyste mohli zjistit, co se v aplikaci v případě problému stalo. Jedním z nejpravděpodobnějších a pravdivých způsobů, jak zachytit informace o tom, co aplikace provádí během chodu, je nechat aplikaci zapisovat, co dělá. Tento proces se označuje jako protokolování. V produkčním prostředí by se v neprodukčním prostředí měly reprodukovány podmínky, za kterých došlo k selhání, a to v produkčním prostředí. Po vhodném přihlášení poskytuje vývojářům plán, jak postupovat v prostředí, které lze testovat a experimentovat s.

### <a name="logging-in-cloud-native-applications"></a>Protokolování v cloudových nativních aplikacích

U každého programovacího jazyka jsou k dispozici nástroje, které umožňují zápis protokolů, a obvykle jsou režie pro zápis těchto protokolů nízká. Mnohé z knihoven protokolování poskytují protokolování různých druhů závažnosti, které mohou být vyladěny v době běhu. Například knihovna Serilog je oblíbená strukturovaná knihovna protokolování pro .NET, která poskytuje následující úrovně protokolování.

* Podrobnosti
* Ladit
* Informace o
* Upozornění
* Chyba
* Závažná

Tyto různé úrovně protokolu poskytují v protokolování členitost. Když aplikace funguje v produkčním prostředí správně, může být nakonfigurována pouze k protokolování důležitých zpráv. Pokud se aplikace nechová, je možné zvýšit úroveň protokolu, aby se shromáždily podrobnější protokoly. To vyvažuje výkon proti snadnému ladění.

Vysoký výkon nástrojů protokolování a tunability podrobností by měl vývojářům přizvat k častému protokolování. Řada upřednostňuje vzor protokolování vstupu a ukončení jednotlivých metod. Tento přístup může být podobný jako přehnaně důkladné, ale je nečastější, že vývojáři budou chtít snížit protokolování. Ve skutečnosti není Neběžné provádět nasazení pouze pro účely přidávání protokolování do problematické metody. Chyba na straně příliš velkého množství protokolování a není příliš malá. Všimněte si, že některé nástroje lze použít k automatickému poskytnutí tohoto typu protokolování.

V tradičních aplikacích se soubory protokolu obvykle ukládají na místním počítači. Ve skutečnosti v operačních systémech, které používají systém UNIX, je definována struktura složek, která bude obsahovat všechny protokoly, obvykle `/var/log`v části. Užitečnost protokolování do plochého souboru na jednom počítači se výrazně snižuje v cloudovém prostředí. Aplikace vytvářející protokoly nemusí mít přístup k místnímu disku nebo je místní disk vysoce přechodný, protože kontejnery jsou v rámci fyzických počítačů přemísťování.

Nativní aplikace v cloudu vyvinuté pomocí architektury mikroslužeb také představují problémy pro protokolovací soubory založené na souborech. Žádosti uživatelů teď můžou zahrnovat několik služeb, které běží na různých počítačích, a můžou zahrnovat funkce bez serveru bez přístupu k místnímu systému souborů. V rámci těchto mnoha služeb a počítačů by bylo velmi náročné korelovat protokoly od uživatele nebo relace.

Nakonec je velký počet uživatelů v některých aplikacích nativních pro Cloud. Představte si, že každý uživatel při přihlášení k aplikaci vygeneruje stovky řádků protokolu. V izolovaném izolaci, který je spravovatelný, ale vynásobte si to více než 100 000 uživatelů a objem protokolů bude velký.

Naštěstí jsou některé alternativy fantastická k použití protokolování založeného na systému souborů. Centralizovaný protokolovací Server, ke kterému jsou odesílány všechny protokoly, řeší všechny tyto problémy. Protokoly jsou shromažďovány aplikacemi a dodávány do centrální protokolovací aplikace, která indexuje a ukládá protokoly. Tato třída systému může každý den ingestovat desítky gigabajtů protokolů.

Při sestavování protokolování, které zahrnuje mnoho služeb, je také užitečné dodržovat některé standardní postupy. Například generování [ID korelace](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) na začátku zdlouhavé interakce a jejich protokolování v každé zprávě, která souvisí s touto interakcí, usnadňuje hledání všech souvisejících zpráv. Jedna zpráva potřebuje najít jenom jednu zprávu a extrahovat ID korelace a najít všechny související zprávy. Dalším příkladem je zajistěte, aby byl formát protokolu pro každou službu stejný, bez ohledu na to, jaký jazyk nebo knihovna protokolů používá. Díky této standardizaci je čtení protokolů mnohem jednodušší. Obrázek 7-1 ukazuje, jak může architektura mikroslužeb využít centralizované protokolování v rámci svého pracovního postupu.

![Protokoly z různých zdrojů se ingestují do centralizovaného úložiště protokolů. **Obrázek 7-1**. ](./media/centralized-logging.png)
 Protokoly z různých zdrojů se ingestují do centralizovaného úložiště protokolů.

## <a name="when-to-use-monitoring"></a>Kdy použít monitorování

Některé aplikace nejsou klíčové. Je možné, že se používají jenom interně, a když dojde k problému, může uživatel kontaktovat odpovědného týmu a aplikace se může restartovat. Zákazníci ale mají často větší očekávání pro aplikace, které spotřebovávají. Potřebujete-li vědět, kdy se aplikace *před* uživateli nebo před tím, než uživatelé budou informovat o problémech, potřebujete monitorovat jeho aktuální stav. Při správné implementaci vám monitorování může informovat o podmínkách, které vedou k problémům, a zajistit tak splnění základních podmínek, které budou mít vliv na všechny uživatele.

## <a name="monitoring-considerations"></a>Důležité informace o monitorování

Některé centralizované systémy protokolování přijímají další roli shromažďování telemetrie mimo čistých protokolů. Můžou shromažďovat metriky, jako je čas pro spuštění databázového dotazu, Průměrná doba odezvy z webového serveru a dokonce i průměr zatížení procesoru a tlak na paměť, který je hlášený operačním systémem. V kombinaci s protokoly můžou tyto systémy poskytovat holistický zobrazení stavu uzlů v systému a aplikace jako celku.

Možnosti shromažďování metriky nástrojů pro monitorování je také možné v rámci aplikace doplňovat ručně. Obchodní toky, které mají zvláštní význam, jako jsou například noví uživatelé registrace nebo objednávky, mohou být instrumentované tak, že zvýší čítač v centrálním monitorovacím systému. To odemkne nástroje pro monitorování, aby nesledovaly jenom stav aplikace, ale i stav podniku.

Dotazy se dají vytvořit v nástrojích pro agregaci protokolů a vyhledat konkrétní statistiky nebo vzory, které se pak dají zobrazit v grafickém formuláři, na vlastních řídicích panelech. Týmy budou často investovat do rozsáhlých displejů připojených k stěnám, které se pohybují prostřednictvím statistik vztahujících se k aplikaci. Tímto způsobem je snadné zobrazit problémy tak, jak se vyskytují.

## <a name="when-to-use-alerts"></a>Kdy použít výstrahy

Pokud potřebujete reagovat na problémy s vaší aplikací, budete potřebovat nějaký způsob, jak upozornit na správné pracovníky. Toto je třetí model závislosti aplikace v nativním cloudu a závisí na protokolování a monitorování. Vaše aplikace musí mít místo přihlášení, aby bylo možné diagnostikovat problémy, a v některých případech předávat do monitorovacích nástrojů. Potřebuje monitorovat agregované metriky aplikací a data o stavu na jednom místě. Jakmile je tato operace navázána, je možné vytvořit pravidla, která aktivují výstrahy, když určité metriky přestanou být mimo přijatelné úrovně.

## <a name="alerts"></a>Upozornění

Můžete vytvářet dotazy na nástroje pro monitorování a hledat tak známé stavy selhání. Dotazy například můžou vyhledat přes příchozí protokoly pro indikaci stavového kódu HTTP 500, což indikuje problém na webovém serveru. Jakmile se zjistí jedna z těchto hodnot, může se e-mailem nebo serverem SMS odeslat vlastníkovi původní služby, která může začít prozkoumat.

Obvykle ale jedna chyba 500 není dostačující k určení toho, že došlo k problému. Může to znamenat, že uživatel nesprávně zadal svoje heslo, nebo zadal některá poškozená data. Dotazy na upozornění se dají vytvořit tak, aby se aktivovaly jenom v případě, že se zjistí větší než průměrný počet chyb 500.

Jedním z nejvíce škodlivých vzorů při upozorňování je vyvolat příliš mnoho výstrah, aby se lidé mohli prozkoumat. Vlastníci služby se rychle odeberou na chyby, které byly dříve prověřené a které byly shledány neškodně. V případě výskytu skutečných chyb pak dojde ke ztrátě hluku stovek falešně pozitivních hodnot. Parable pro [Boy, kteří provedli Jillian,](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) se často dozvěděli dětem, aby jim upozornili na toto velmi nebezpečné. Je důležité zajistit, aby výstrahy, které se aktivují, byly indikativní pro skutečný problém.

>[!div class="step-by-step"]
>[Předchozí](monitoring-health.md)
>[Další](logging-with-elastic-stack.md)
