---
title: "Základy kolekce paměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
caps.latest.revision: "51"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15ae041cdadb259c59d447b8775844fc96048be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="fundamentals-of-garbage-collection"></a>Základy kolekce paměti
<a name="top"></a>V common language runtime (CLR) bude systém uvolňování slouží jako správce automatické paměti. Poskytuje následující výhody:  
  
-   Umožňuje vyvíjet aplikaci bez nutnosti volné paměti.  
  
-   Objekty v spravovaná halda přiděluje efektivně.  
  
-   Získá objekty, které se již nepoužívají, vymaže jejich paměť a zajišťuje dostupné pro budoucí přidělení paměti. Spravované objekty automaticky začínat, získat čistou obsah, takže jejich konstruktory nemají k chybě při inicializaci každé datové pole.  
  
-   Poskytuje bezpečnost paměti tím, že zajistí, že objekt nelze použít obsah jiného objektu.  
  
 Toto téma popisuje základní koncepty uvolnění paměti. Obsahuje následující oddíly:  
  
-   [Základní informace o paměti](#fundamentals_of_memory)  
  
-   [Podmínky pro kolekci paměti](#conditions_for_a_garbage_collection)  
  
-   [Spravovaná halda](#the_managed_heap)  
  
-   [Generace](#generations)  
  
-   [Co se stane, že během uvolňování paměti](#what_happens_during_a_garbage_collection)  
  
-   [Manipulace s nespravovaných prostředků](#manipulating_unmanaged_resources)  
  
-   [Uvolňování paměti serveru a pracovní stanice](#workstation_and_server_garbage_collection)  
  
-   [Souběžné uvolňování paměti](#concurrent_garbage_collection)  
  
-   [Kolekce paměti na pozadí pracovní stanice](#background_garbage_collection)  
  
-   [Kolekce paměti na pozadí serveru](#background_server_garbage_collection)  
  
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Základní informace o paměti  
 Následující seznam shrnuje důležité koncepty paměti CLR.  
  
-   Každý proces má svou vlastní, samostatné virtuální adresní prostor. Všechny procesy ve stejném počítači sdílet stejnou fyzickou paměť a sdílet stránkovací soubor, pokud existuje.  
  
-   Každý proces ve výchozím nastavení v počítačích 32-bit, má virtuální adresní prostor uživatelského režimu 2 GB.  
  
-   Jako vývojář aplikací fungovat jenom s virtuální adresní prostor a nikdy pracovat přímo s fyzické paměti. Uvolňování paměti přidělí a uvolní virtuální paměti pro vás na spravovaná halda.  
  
     Pokud vytváříte nativní kód, použijete Win32 funkce pro práci s virtuální adresní prostor. Tyto funkce přidělit a haldách volné virtuální paměti pro vás na nativní.  
  
-   Virtuální paměti může být v tří stavů:  
  
    -   Bezplatná. Blok paměti obsahuje žádné odkazy na ni a je k dispozici pro přidělení.  
  
    -   Vyhrazena. Na oblast paměti je k dispozici pro vaše použití a nelze použít pro další požadavek přidělení. Dokud se zavazuje však nelze ukládat data do tohoto bloku paměti.  
  
    -   Potvrdí. Blok paměti je přiřazený k fyzické úložiště.  
  
-   Můžete získat fragmentované virtuální adresní prostor. To znamená, že existují volné blokuje, také známé jako díry v adresním prostoru. Pokud se požaduje přidělení virtuální paměti, musí nástroj virtual memory manager najít jeden blok volné dostatečně velký na to, aby pokryl tento požadavek na přidělení. I v případě, že máte 2 GB volného místa, přidělení, která vyžaduje 2 GB neúspěšné, pokud všechny tohoto volného místa v bloku jednu adresu.  
  
-   Pokud spustíte mimo virtuální adresní prostor tak, aby vyhradil nebo potvrzení fyzického místa na disku můžete spustit nedostatek paměti.  
  
 Stránkovacího souboru se používá i v případě přetížení fyzické paměti (to znamená, že poptávka po fyzické paměti) je nízká. Při prvním přetížení vaše fyzické paměti je vysoká, operační systém musí uvolnil prostor ve fyzické paměti k ukládání dat a zálohuje některá data, která je ve fyzické paměti do souboru stránky. Dokud není stránkovaného dat je potřeba, takže je možné setkat stránkování v situacích, kde je velmi nízkou přetížení fyzické paměti. 
 
 [Zpět na začátek](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Podmínky pro kolekci paměti  
 Uvolňování paměti dojde, pokud je splněna jedna z následujících podmínek:  
  
-   Systém má nízké fyzické paměti. To je zjištěna oznámení nedostatek paměti z operačního systému nebo nedostatek paměti indikován hostitele.
  
-   Paměť, která je používána přidělené objekty v spravovaná halda převyšuje přípustnou mezní hodnotu. Tato prahová hodnota se neustále upraví proces běží.  
  
-   <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána. Ve většině případů není nutné volat tuto metodu, protože uvolňování paměti běží nepřetržitě. Tato metoda se používá hlavně pro jedinečný situace a testování.  
  
 [Zpět na začátek](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>Spravovaná halda  
 Po uvolňování paměti se inicializuje pomocí modulu CLR, přiděluje segment paměti k ukládání a správě objektů. Této paměti se nazývá spravovaná halda oproti nativní haldy v operačním systému.  
  
 Je spravovaná halda pro každý spravovaný proces. Všechna vlákna v procesu přidělit paměť pro objekty v haldě stejné.  
  
 Můžete vyhradit paměť, bude systém uvolňování volání Win32 [VirtualAlloc](http://go.microsoft.com/fwlink/?LinkId=179047) funkce a jeden segment rezervy paměti v době spravovaných aplikací. Uvolňování paměti také si vyhrazuje segmenty podle potřeby a uvolní segmenty zpět do operačního systému (po vymazání je všechny objekty) voláním Win32 [virtualfree –](http://go.microsoft.com/fwlink/?LinkId=179050) funkce.  
  
> [!IMPORTANT]
>  Velikost segmentů přidělené modulem garbage collector závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace. Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.  
  
 Menší počet objektů přidělené v haldě menší práci, kterou uvolňování paměti má udělat. Při přidělování objektů, nepoužívejte zaokrouhlené hodnot, které přesahují vašim potřebám, jako je přidělování pole 32 bajtů, pokud budete potřebovat pouze 15 bajtů.  
  
 Když se aktivuje uvolňování paměti získá má systém uvolňování paměti, která je zaneprázdněn neaktivní objekty. Proces reclaiming zkomprimuje živé objekty tak, aby se přesouvají společně a odebere neaktivní místa, a díky halda menší. Tím se zajistí, že objekty, které jsou přiděleny společně pohromadě na spravované haldě, chcete-li zachovat jejich polohu.  
  
 Míra interakce (četnost a doba trvání) kolekce je výsledek objem přidělení a množství paměti zůstal naživu na spravované haldě.  
  
 Halda lze považovat za nahromadění dvě haldách: halda velkého objektu a halda malé objektu.  
  
 Halda velkého objektu obsahuje velké objekty, které jsou 85,000 bajtů nebo větší. Pole jsou obvykle objekty v haldě velkého objektu. Je obvyklé, aby objekt instance tak, aby se velmi velký.  
  
 [Zpět na začátek](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Generace  
 Halda jsou uspořádány do generace, takže je může zpracovat objekty dlohotrvající a krátkodobou. Především dojde k uvolnění paměti s recyklaci krátkodobou objektů, které obvykle zabírají pouze malou část toho haldě. Existují tři generace sady objektů v haldě:  
  
-   **Generace 0**. Toto je nejmladšího generování a obsahuje krátkodobou objekty. Příklad krátkodobou objektu je dočasný proměnné. Nejčastěji v generování dojde k uvolnění paměti.  
  
     Nově přidělených objekty vytvoří nové generace objektů a jsou implicitně 0. generace kolekce, které nejsou rozsáhlé objekty, v takovém případě přejděte v haldě rozsáhlý objekt v kolekci 2. generace.  
  
     Většinu objektů se uvolní pro uvolňování paměti v 0. generace a není zachována i po ukončení pro příští generaci.  
  
-   **Generace 1**. Generování obsahuje krátkodobou objekty a slouží jako vyrovnávací paměť mezi krátkodobou a dlohotrvající objekty.  
  
-   **Generace 2**. Generování obsahuje dlohotrvající objekty. Příklad dlohotrvající objektu je objekt v aplikaci serveru, který obsahuje statických dat, který je za provozu pro dobu trvání procesu.  
  
 Probíhalo uvolňování paměti na konkrétní generace jako vlastní podmínky. Shromažďování generování znamená shromažďování objekty v této generaci a všechny jeho mladší generace. Uvolnění paměti generace 2 se taky říká kolekce úplného uvolňování paměti, protože ji získá všechny objekty ve všech generací (to znamená, že všechny objekty v spravovaná halda).  
  
### <a name="survival-and-promotions"></a>Základními a reklamními nabídkami  
 Objekty, které nejsou uvolnit v kolekci paměti se označuje jako přesun a povýšené na nové generace. Objekty, které zůstanou platné i po generace 0 uvolňování povýšené na generace 1; objekty, které zůstanou platné i po generace 1 uvolňování povýšené na generaci 2; a objekty, které zůstanou platné i po uvolnění paměti generace 2 zůstanou v 2. generace.  
  
 Při uvolňování zjistí, že je základními frekvence vysoká v generaci, jeho hodnota se zvyšuje prahová hodnota přidělení pro této generaci, takže další kolekce získá významné velikost paměti regenerovaný. Modul CLR průběžně vyrovnává dvě priority: není umožníte aplikace je práce sadu get příliš velké a ne umožníte uvolňování trvat příliš dlouho.  
  
### <a name="ephemeral-generations-and-segments"></a>Dočasné generace a segmentů  
 Protože objekty v generace 0 a 1 jsou krátkodobou, tyto generace jsou známé jako dočasné generace.  
  
 Dočasné generace musí být přidělena v paměti segment, který se označuje jako dočasné segmentu. Každý nový segment získali modulem garbage collector stane nové dočasné segmentu a obsahuje objekty, které zůstal naživu uvolňování 0. generace. Segment nové generace 2 se změní na staré dočasné segmentu.  
  
 Velikost dočasné segmentu se liší podle toho, jestli systém je 32 - nebo 64bitová verze a na typu systém uvolňování paměti, které je spuštěná. V následující tabulce jsou uvedeny výchozí hodnoty.  
  
||32bitová|64bitových|  
|-|-------------|-------------|  
|Pracovní stanice uvolňování paměti|16 MB|256 MB|  
|Server globálního katalogu|64 MB|4 GB|  
|Server globálního katalogu s > 4 logické procesory|32 MB|2 GB|  
|Server globálního katalogu s > 8 logické procesory|16 MB|1 GB|  
  
 Dočasné segment může obsahovat objekty 2. generace. Objekty 2. generace, můžete použít několik segmentů (libovolný počet. vyžaduje váš proces a umožňuje paměti).  
  
 Množství uvolněné paměti z uvolnění dočasné paměti je omezeno na velikost dočasné segmentu. Množství paměti, který je uvolněn je úměrná prostor, který byl zaneprázdněn neaktivní objekty.  
  
 [Zpět na začátek](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>Co se stane, že během uvolňování paměti  
 Uvolňování paměti má tyto fáze:  
  
-   Fáze označení, která vyhledá a vytvoří seznam všech objektů za provozu.  
  
-   Relocating fázi, která aktualizuje odkazy na objekty, které budou probíhat.  
  
-   Fáze komprimaci, který získá místo obsazena neaktivní objekty a zkomprimuje zbývající objekty. Fázi komprimaci přesune objekty, které mají zůstal naživu kolekce paměti na konci starší segmentu.  
  
     Protože 2. generace kolekce může zabírat několik segmentů, objekty, které jsou povýší do 2. generace se dají přesunout do starší segmentu. Generace 1 i generace 2 přesun můžete přesunout na jiný segment, protože jsou povýšen na 2. generace.  
  
     Normálně není zkomprimovanou haldě velkého objektu, protože kopírování velkých objektů výrazně snižuje výkon. Ale začínající [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], můžete použít <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost kompaktních velkého objektu haldy na vyžádání.  
  
 Uvolňování paměti používá tyto informace k určení, zda jsou objekty za provozu:  
  
-   **Zásobník kořeny**. Proměnné zásobníku poskytované kompilátoru za běhu (JIT) a walkera zásobníku.  
  
-   **Kolekce popisovačů paměti**. Zpracuje, že bod pro spravované objekty a že může být přidělen pomocí uživatelského kódu nebo modul common language runtime.  
  
-   **Statických dat**. Statické objekty v doménách aplikace, které by mohly být odkazující na jiné objekty. Každou doménu aplikace uchovává informace o jeho statické objekty.  
  
 Před zahájením uvolnění paměti, jsou všechny spravovaných vláknech pozastavené s výjimkou vláken, který aktivoval uvolnění paměti.  
  
 Následující obrázek znázorňuje vláken, který aktivuje uvolnění paměti a způsobí, že jiná vlákna pozastaví.  
  
 ![Když vlákno aktivuje uvolnění paměti](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Vlákno, které aktivuje kolekce paměti  
  
 [Zpět na začátek](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Manipulace s nespravovaných prostředků  
 Pokud spravované objekty odkazovat na nespravované objekty pomocí jejich obslužných rutin souborů nativní, musíte explicitně uvolnit nespravované objekty, protože má systém uvolňování paměti sleduje pouze na spravovaná halda.  
  
 Uživatelé spravovaného objektu nemusí dispose nativní prostředky využívané objektem. Můžete provést vymazání, můžete provést spravovaného objektu finalizable. Finalizace se skládá z akce čištění, které můžete provést při objekt je již používán. Když spravovaného objektu kterou, provede akce čištění, které jsou určené v jeho metoda finalizační metodu.  
  
 Pokud objekt finalizable byla vyhodnocena jako neaktivní, jeho finalizační metodu je vložen do fronty, aby provedení akcí čištění, ale samotný objekt je propagována do nové generace. Proto je nutné čekat na další uvolňování paměti, ke kterému dochází v této generaci (který není nutně další uvolňování) k určení, zda byl uvolněn objekt.  
  
 [Zpět na začátek](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>Uvolňování paměti serveru a pracovní stanice  
 Uvolňování paměti je vlastního vyladění a může fungovat v celé řadě scénářů. Soubor nastavení konfigurace můžete nastavit typ uvolňování paměti na základě charakteristik pracovního vytížení. Modul CLR poskytuje následující typy uvolňování paměti:  
  
-   Kolekce paměti pracovní stanice, která je pro všechny klientské pracovní stanice a samostatné počítače. Toto je výchozí nastavení [ \<gcserver – > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ve schématu konfigurace modulu runtime.  
  
     Uvolňování paměti pracovní stanice může být souběžných nebo nesouběžného. Souběžné uvolňování paměti umožňuje spravovaných vláknech, chcete-li pokračovat v operacích během uvolňování paměti.  
  
     Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kolekce paměti na pozadí nahrazuje souběžné uvolňování paměti.  
  
-   Kolekce paměti na serveru, který je určený pro serverové aplikace, které je třeba vysoké propustnosti a škálovatelnost. Kolekce paměti na serveru může být nesouběžného nebo na pozadí.  
  
 Následující obrázek znázorňuje vyhrazené vláken, která provést kolekce paměti na serveru.  
  
 ![Server paměti kolekce vláken](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Kolekce paměti na serveru  
  
### <a name="configuring-garbage-collection"></a>Konfigurace uvolňování paměti  
 Můžete použít [ \<gcserver – > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) schématu konfigurace modulu runtime pro určení typu uvolňování paměti, kterou chcete CLR k provedení. Když tento element `enabled` je nastavena na hodnotu `false` (výchozí), modul CLR provádí uvolňování paměti pracovních stanic. Když nastavíte `enabled` atribut `true`, modul CLR provede kolekce paměti na serveru.  
  
 Souběžné uvolňování paměti je definován s [ \<gcconcurrent – > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) schématu konfigurace modulu runtime. Ve výchozím nastavení je `enabled`. Toto nastavení určuje, jak souběžných a uvolňování paměti na pozadí.  
  
 Také můžete určit kolekce paměti na serveru s nespravovaná hostingu rozhraní. Všimněte si, že technologie ASP.NET a SQL Server povolení kolekce paměti na serveru automaticky pokud je vaše aplikace hostována v některém z těchto prostředí.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>Porovnání uvolňování paměti serveru a pracovní stanice  
 Dělení na vlákna a výkonu aspekty uvolňování paměti pracovní stanice jsou následující:  
  
-   Kolekce proběhne uživatelské vlákno, který aktivoval uvolňování paměti a zůstanou v se stejnou prioritou. Protože vlákna uživatelského obvykle běží s normální prioritou, musí uvolňování paměti (který se spouští ve vlákně s normální prioritou) pokouší o času procesoru s jiná vlákna.  
  
     Nejsou pozastavit vláken, které jsou spuštěny nativního kódu.  
  
-   Uvolňování paměti pracovních stanic se vždy používá na počítač, který obsahuje pouze jeden procesor, bez ohledu na to [ \<gcserver – >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) nastavení. Pokud zadáte kolekce paměti na serveru, modul CLR používá uvolňování paměti pracovních stanic s souběžnosti zakázána.  
  
 Dělení na vlákna a výkonu aspekty kolekce paměti na serveru jsou následující:  
  
-   Kolekce proběhne více vyhrazených vláken, které jsou spuštěné v `THREAD_PRIORITY_HIGHEST` úroveň priority.  
  
-   Haldu a vyhrazené vlákno k provedení uvolňování paměti jsou k dispozici pro každý procesor a haldách se shromažďují ve stejnou dobu. Každý haldy obsahuje malé objektu haldy a velkého objektu haldy, a všech haldách je přístupný pomocí uživatelského kódu. Objekty umístěné na různých haldách mohou odkazovat na sebe navzájem.  
  
-   Protože více vláken kolekce paměti spolupracují, kolekce paměti na serveru je rychlejší než uvolňování paměti pracovních stanic v haldě stejnou velikost.  
  
-   Často kolekce paměti na serveru má větší velikost segmentů. Upozorňujeme však, že se jedná pouze generalizace: velikost segmentu závisí na implementaci a mohou podléhat změnám. Měl by žádné předpoklady o velikosti segmentů přidělený modulem garbage collector při ladění aplikace.  
  
-   Kolekce paměti na serveru může být náročná. Například pokud máte 12 procesů spuštěných na počítači, který má 4 procesory, budou existovat 48 vláken kolekce vyhrazené paměti Pokud se používá kolekce paměti na serveru. V situaci, zatížení velkého množství paměti spuštění všech procesů díky uvolňování paměti, bude mít uvolňování 48 vláken při plánování.  
  
 Pokud používáte stovky instance aplikace, zvažte použití uvolňování paměti pracovních stanic s souběžné uvolňování zakázána. Výsledkem bude menší přepínání kontextu, což může zlepšit výkon.  
  
 [Zpět na začátek](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Souběžné uvolňování paměti  
 V uvolňování paměti pracovních stanicích nebo serverech můžete povolit souběžné uvolňování paměti, která umožňuje podprocesů pro spuštění souběžně vyhrazené vlákno, které provede uvolnění paměti pro většinu doby trvání kolekce. Tato možnost ovlivní pouze kolekce, uvolňování paměti v generaci 2; generace 0 a 1 jsou vždy nesouběžného, protože se dokončit velmi rychle.  
  
 Souběžné uvolňování paměti umožňuje interaktivní aplikace jako více odpovídající pomocí minimalizace pozastaví pro kolekci. Spravovaných vláknech můžete nadále spouštět většinu času při souběžné uvolňování paměti kolekce vlákno je spuštěno. Výsledkem kratší pozastaví při dochází k uvolnění paměti.  
  
 Chcete-li zvýšit výkon, pokud jsou spuštěny několik procesy, zakažte souběžné uvolňování paměti. To provedete tak, že přidáte [ \<gcconcurrent – > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurační soubor aplikace a nastavení hodnoty jeho `enabled` atribut `"false"`.  
  
 Souběžné uvolňování paměti se provádí na vyhrazené vlákno. Ve výchozím nastavení spouští modulu CLR uvolňování paměti pracovních stanic s souběžné uvolňování povolena. To platí pro počítače, jeden a více procesorů.  
  
 Schopnost přidělit malých objektů v haldě během souběžné uvolňování je omezena na dočasný segment vlevo, když se spustí souběžné uvolňování objektů. Také můžete dosáhnout konce segmentu, je nutné čekat na souběžné uvolňování ukončíte spravovaných vláken, která nutné provést přidělení malé objektu je pozastaven.  
  
 Souběžné uvolňování má mírně větší pracovní sada (ve srovnání s nesouběžného uvolňování paměti), protože objekty můžete přidělit během souběžných kolekce. Ale to může ovlivnit výkon, protože objekty, které přidělíte stane součástí pracovní sady. V podstatě souběžné uvolňování obchoduje některé procesoru a paměti pro kratší pozastaví.  
  
 Následující obrázek znázorňuje souběžné uvolňování paměti na samostatný vyhrazený podproces provést.  
  
 ![Souběžné uvolňování paměti kolekce vláken](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Souběžné uvolňování paměti  
  
 [Zpět na začátek](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Kolekce paměti na pozadí pracovní stanice  
 V kolekce paměti na pozadí se shromažďují dočasné generace (0 a 1) podle potřeby, když probíhá kolekce 2. generace. Neexistuje žádné nastavení pro kolekce paměti na pozadí; je automaticky povolen s souběžné uvolňování paměti. Kolekce paměti na pozadí je náhradou za souběžné uvolňování paměti. Jako s souběžné uvolňování paměti, kolekce paměti na pozadí se provádí na vyhrazené vláken a se vztahuje pouze na 2. generace kolekce.  
  
> [!NOTE]
>  Kolekce paměti na pozadí je k dispozici pouze v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a novějších verzích. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je podporována pouze pro uvolňování paměti pracovních stanic. Od verze rozhraní .NET Framework 4.5, je k dispozici pro uvolňování paměti serveru a pracovní stanice kolekce paměti na pozadí.  
  
 Kolekce na dočasné generace během kolekce paměti na pozadí se označuje jako uvolňování paměti popředí. Pokud dojde k kolekce popředí, jsou všechny spravovaných vláknech pozastavené.  
  
 Když jste přidělili dostatečný počet objektů v 0. generace kolekce paměti na pozadí probíhá, provede modulu CLR generace 0 nebo 1 popředí generace uvolňování paměti. Vlákno kolekce paměti vyhrazené pozadí kontroluje v časté bezpečné body k určení, zda je žádost pro uvolňování paměti popředí. Pokud existuje, kolekci pozadí pozastaví sám sebe, tak, aby uvolňování paměti popředí může dojít. Po dokončení uvolňování popředí vlákna kolekce paměti vyhrazené pozadí a vlákna uživatelského obnovit.  
  
 Kolekce paměti na pozadí odebere omezení přidělení určeného souběžné uvolňování paměti, protože kolekce dočasné paměti může dojít během kolekce paměti na pozadí. To znamená, že můžete odebrat neaktivní objekty v dočasných generace kolekce paměti na pozadí a můžete také rozšířit halda v případě potřeby během uvolňování 1. generace.  
  
 Následující obrázek znázorňuje kolekce paměti na pozadí provést na samostatném vyhrazeném vlákně na pracovní stanici.  
  
 ![Uvolňování paměti pracovních stanic na pozadí](../../../docs/standard/garbage-collection/media/backgroundworkstn.png "BackgroundWorkstn")  
Kolekce paměti na pozadí pracovní stanice  
  
 [Zpět na začátek](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Kolekce paměti na pozadí serveru  
 Od verze rozhraní .NET Framework 4.5, kolekce paměti na pozadí serveru je výchozí režim pro uvolňování paměti serveru. Chcete-li zvolit tento režim, nastavte `enabled` atribut [ \<gcserver – > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) k `true` ve schématu konfigurace modulu runtime. Uvolňování paměti pracovních stanic pozadí, tato funkce režimu podobně popsané v předchozí části, ale existuje několik rozdílů. Uvolňování paměti pracovních stanic pozadí používá jedno vlákno kolekce paměti vyhrazené pozadí, zatímco kolekce paměti na pozadí serveru používá více vláken, obvykle vyhrazené vlákno pro každý logický procesor. Na rozdíl od pracovní stanice vlákně na pozadí paměti kolekce tyto vláken nikdy nevyprší.  
  
 Následující obrázek znázorňuje kolekce paměti na pozadí na samostatný vyhrazený podproces na serveru provést.  
  
 ![Kolekce paměti na serveru na pozadí](../../../docs/standard/garbage-collection/media/backgroundserver.png "BackgroundServer")  
Kolekce paměti na pozadí serveru  
  
## <a name="see-also"></a>Viz také  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
