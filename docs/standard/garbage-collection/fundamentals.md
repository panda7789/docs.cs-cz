---
title: Základy kolekce paměti
description: Zjistěte, jak funguje systému uvolňování paměti a jak ho lze konfigurovat pro optimální výkon.
ms.date: 03/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d3ac6acf756a0ac468eb4483432467429ed91ca
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483285"
---
# <a name="fundamentals-of-garbage-collection"></a>Základy kolekce paměti
<a name="top"></a> V modulu common language runtime (CLR) slouží systému uvolňování paměti jako automatický správce paměti. Poskytuje následující výhody:  
  
- Umožňuje vývoj aplikace, aniž by bylo nutné uvolnit paměť.  
  
- Efektivně přiděluje objekty ve spravované haldě.  
  
- Uvolní objekty, které jsou již nejsou déle používány, vymaže jejich paměť a udržuje k dispozici pro budoucí přidělení paměti. Spravované objekty automaticky se získat čistý obsah, takže jejich konstruktory nemusejí inicializovat všechna datová pole.  
  
- Zajišťuje bezpečnost paměti a ujistěte se, že objekt nemůže použít obsah jiného objektu.  
  
 Toto téma popisuje základní koncepty uvolňování paměti. 
 
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Základní informace o paměti  
 Následující seznam shrnuje důležité pojmy paměti CLR.  
  
- Každý proces má svůj vlastní samostatný virtuální adresní prostor. Všechny procesy ve stejném počítači sdílejí stejnou fyzickou paměť a stránkovací soubor sdílet, pokud existuje.  
  
- Každý proces má ve výchozím nastavení se na 32bitových počítačích uživatelského režimu 2 GB virtuálního adresového prostoru.  
  
- Jako vývojář aplikace pracujete pouze s virtuálním adresovým prostorem a nikdy pracovat přímo s fyzickou paměť. Uvolňování paměti přiděluje a uvolňuje virtuální paměť můžete na spravované haldě.  
  
     Při psaní nativního kódu používáte funkce Win32 pro práci s virtuálním adresovým prostorem. Tyto funkce přidělují a uvolňují virtuální paměť pro vás na nativních haldách.  
  
- Virtuální paměť může být ve třech stavech:  
  
    - Zdarma. Blok paměti nemá žádné odkazy a je k dispozici pro přidělení.  
  
    - Vyhrazená. Blok paměti je k dispozici pro použití a nelze použít pro všechny další požadavky na přidělení. Dokud nebude potvrzena změna, ale nemůže uložit data do tohoto bloku paměti.  
  
    - Potvrzené. Blok paměti je přiřazen fyzickému úložišti.  
  
- Virtuální adresový prostor se může fragmentovat. To znamená, že existují volné blokuje známé také jako otvory v adresním prostoru. Pokud se požaduje přidělení virtuální paměti, správce virtuální paměti musí najít jeden volný blok, který je dostatečně velký, aby splňují tento požadavek na přidělení. I v případě, že máte 2 GB volného místa, přidělení vyžadující 2 GB neúspěšné, pokud je všechno toto volné místo je v jednom bloku adres.  
  
- Můžete zjistit nedostatek paměti Pokud vyčerpáte virtuálního adresového prostoru pro rezervaci nebo fyzické místo pro potvrzení.  
  
 Stránkovací soubor se používá i v případě, že je nízký tlak fyzické paměti (to znamená poptávka po fyzické paměti). Při prvním vaše tlak fyzické paměti je vysoké, operační systém musí uvolnit prostor fyzické paměti k ukládání dat a jejich zálohování a některá data, která je ve fyzické paměti stránkovacího souboru. Že data nejsou stránkována, dokud není třeba, takže je možné se setkat stránkování v situacích, kde je velmi nízký tlak fyzické paměti. 
 
 [Zpět na začátek](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Podmínky pro uvolnění paměti  
 Uvolnění paměti dojde, pokud je splněna jedna z následujících podmínek:  
  
- Systém má nedostatek fyzické paměti. To zjistí oznámení nedostatek paměti z operačního systému nebo nedostatek paměti indikován hostitele.
  
- Paměť, která se používají přidělené objekty na spravované haldě překročí přijatelný práh. Tento práh se neustále upravuje, proces běží.  
  
- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána. V téměř všech případech není nutné volat tuto metodu, protože systému uvolňování paměti běží nepřetržitě. Tato metoda se používá především pro unikátní situace a testování.  
  
 [Zpět na začátek](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>Spravovaná halda  
 Po inicializaci uvolňování paměti modulem CLR přidělí paměti k ukládání a správě objektů. Tato paměť se nazývá spravovaná halda, oproti nativní haldě v operačním systému.  
  
 Existuje spravovaná halda pro každý spravovaný proces. Všechna vlákna v procesu přidělují paměť objektům ve stejné haldě.  
  
 Pro vyhrazení paměti, uvolňování paměti volá Win32 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) funkce a rezervuje jeden segment paměti pro spravované aplikace. Uvolňování také rezervuje segmentů podle potřeby a uvolní segmenty zpět do operačního systému (po jejich vymazání ze všech objektů) voláním rozhraní Win32 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) funkce.  
  
> [!IMPORTANT]
>  Velikost segmentů přidělaná systému uvolňování paměti je specifický pro implementaci a může se změnit kdykoli, včetně v pravidelné aktualizace. Vaše aplikace by nikdy vytvořit předpoklady o nebo závisí na velikosti konkrétního segmentu, ani snažit konfigurace množství paměti k přidělení segmentu.  
  
 Čím méně je objektů přidělených do, tím méně práce systém uvolňování paměti má udělat. Při přidělování objektů nepoužívejte zaokrouhlené hodnoty, které přesahují vaše potřeby, například přidělování matice 32 bajtů, když potřebujete pouze 15 bajtů.  
  
 Při spuštění procesu uvolnění paměti získá systém uvolňování paměti, která je obsazenou neživými objekty. Proces recyklování zkomprimuje živé objekty tak, aby se přesunuly dohromady, a mrtvý prostor je odebrán, díky čemuž haldy menší. Tím se zajistí, že objekty, které jsou přiděleny společně zůstanou pohromadě na spravované haldě, aby se zachovalo jejich místo.  
  
 Intrusiveness (četnost a doba trvání) uvolnění paměti je výsledkem objem přidělení a množství paměti naživu na spravované haldě.  
  
 Halda může být považována za souběh dvou hald: [haldy pro velké objekty](large-object-heap.md) a haldy malých objektů.  
  
 [Haldy pro velké objekty](large-object-heap.md) obsahují velmi velké objekty o velikosti 85 000 bajtů a větší. Pole jsou obvykle objekty na velkých objektových haldách. Navíc není obvyklé velmi velká instance objektu.  
  
 [Zpět na začátek](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Generace  
 Haldy jsou uspořádány do generací, takže mohou zpracovat objekty s dlouhou a krátkou životností. Uvolňování paměti dochází především u regenerace krátkodobých objektů, které obvykle zabírají pouze malou část haldy. Existují tři generace objektů na haldě:  
  
- **Generace 0**. To je nejmladší generace a obsahuje krátkodobé objekty. Příkladem objektu krátkodobou je dočasná proměnná. Uvolňování paměti dochází nejčastěji v této generaci.  
  
     Nově přidělené objekty tvoří novou generaci objektů a jsou implicitně kolekcemi generace 0, pokud se nejedná o velké objekty, ve kterémžto případě přejdou na haldy pro velké objekty v kolekci generace 2.  
  
     Většina objektů je získána pro uvolnění paměti v generaci 0 a nepřežije do další generace.  
  
- **1. generace**. Tato generace obsahuje krátkodobé objekty a slouží jako vyrovnávací paměť mezi krátkodobými a dlouhodobými objekty.  
  
- **2. generace**. Tato generace obsahuje objekty s dlouhým poločasem rozpadu. Příkladem objektu s dlouhým poločasem rozpadu je objekt v serverové aplikaci obsahující statická data, která jsou živá po dobu trvání procesu.  
  
 Důvodu podmínek, dojde k uvolnění paměti u konkrétních generací. Sběr generace znamená shromažďování objektů dané generace a všech mladších generací. Uvolnění paměti generace 2 se také nazývá úplné uvolnění paměti, protože ji získají všechny objekty ve všech generacích (to znamená, že všechny objekty ve spravované haldě).  
  
### <a name="survival-and-promotions"></a>Přežití a propagační akce  
 Objekty, které nejsou uvolněny v procesu uvolnění paměti se nazývají zachované objekty a jsou povýšeny do příští generace. Objekty, které byly zachovány při uvolnění generace 0 jsou povýšeny do generace 1; objekty, které byly zachovány při uvolnění 1. generace jsou povýšeny do generace 2. a objekty, které byly zachovány při uvolnění paměti generace 2 zůstanou v generaci 2.  
  
 Při uvolňování paměti zjistí, že míra přežití je v generaci vysoká, zvýší práh alokací pro tuto generaci, takže další kolekce získá značnou velikost regenerované paměti. CLR neustále vyrovnává dvě priority: aby aplikace pracovní sada příliš nezvětšila a neumožnit umožňuje uvolňování paměti kolekce trvat příliš dlouho.  
  
### <a name="ephemeral-generations-and-segments"></a>Dočasné generace a segmenty  
 Protože objekty v generacích 0 a 1 jsou krátkodobé, jsou tyto generace označovány jako dočasné generace.  
  
 Dočasné generace musí být přiděleny v segmentu paměti, který je známý jako dočasný segment. Každý nový segment získaný systému uvolňování paměti stane novým dočasným segmentem a obsahuje objekty, které zůstat naživu při uvolňování 0. generace. Starý dočasný segment se stane segmentem nové generace 2.  
  
 Velikost dočasného segmentu se liší v závislosti na tom, zda je systém 32 - a 64-bit a na druhu systému uvolňování paměti, kterým je spuštěný. Výchozí hodnoty jsou uvedeny v následující tabulce.  
  
||32bitová|64bitová|  
|-|-------------|-------------|  
|Uvolňování paměti pracovní stanice|16 MB|256 MB|  
|Server globálního katalogu|64 MB|4 GB|  
|Uvolňování paměti serveru pomocí > 4 logické procesory|32 MB|2 GB|  
|Uvolňování paměti serveru pomocí > 8 logické procesory|16 MB|1 GB|  
  
 Dočasný segment může obsahovat objekty generace 2. Objekty 2. generace můžete použít více segmentů (tolik, váš proces vyžaduje a paměť umožňuje).  
  
 Množství uvolněné paměti z kolekce uvolnění dočasné paměti je omezeno na velikost dočasného segmentu. Množství paměti, která je uvolněna, je úměrná místu, které byla obsazeno neživými objekty.  
  
 [Zpět na začátek](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>Co se stane během uvolňování paměti  
 Uvolnění paměti má následující fáze:  
  
- Fáze označení, která zjistí a vytvoří seznam všech živých objektů.  
  
- Fáze přemístění, která aktualizuje odkazy na objekty, které budou komprimovány.  
  
- Komprimační fáze, která uvolňuje místo obsazené nepoužívanými objekty a komprimuje zbývající objekty. Fáze komprimace přesune objekty, které mají zůstat naživu při uvolňování paměti ve starším konci segmentu.  
  
     Protože kolekce generace 2 mohou zabírat více segmentů, objekty, které jsou povýšeny do generace 2 je přesunout do starší segmentu. Generace 1 i 2 zachovalých můžete přesunout do jiného segmentu, protože jsou povýšeny do generace 2.  
  
     Obvykle není setřepána halda velkého objektu, protože kopírování velkých objektů výrazně snižuje výkon. Nicméně od verze rozhraní .NET Framework 4.5.1, můžete použít <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost ke komprimaci haldy pro velké objekty na vyžádání.  
  
 Uvolňování paměti používá tyto informace k určení, zda jsou objekty živé:  
  
- **Kořeny zásobníku**. Proměnné zásobníku poskytované just-in-time (JIT) kompilátorem a zásobníkem. Všimněte si, že optimalizace JIT může prodloužit nebo zkrátit oblasti kódu v rámci které zásobníku proměnné hlášení do systému uvolňování paměti.
  
- **Obslužné rutiny uvolnění paměti**. Zajišťuje, že směrující na spravované objekty a které mohou být přiděleny podle uživatelského kódu nebo modul common language runtime.  
  
- **Statická data**. Statické objekty v aplikačních doménách, které by mohly odkazovat na jiné objekty. Každá aplikační doména uchovává informace o svých statických objektech.  
  
 Před zahájením procesu uvolnění paměti jsou všechna spravovaná vlákna pozastavena, s výjimkou vlákna, které spustí uvolnění.  
  
 Následující obrázek znázorňuje vlákno, které spustí uvolnění paměti a způsobí, že pozastaví ostatní vlákna.  
  
 ![Při aktivaci vlákno kolekce uvolnění paměti](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Podproces, který spustí uvolnění paměti  
  
 [Zpět na začátek](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Manipulace s nespravovanými prostředky  
 Pokud vaše spravované objekty odkazují na nespravované objekty pomocí nativních popisovačů souborů, musíte explicitně uvolnit nespravované objekty, protože systém uvolňování paměti sleduje pouze na spravované haldě.  
  
 Uživatelé vašeho spravovaného objektu nemusí mít nativní prostředky používané tímto objektem. Chcete-li provádět vyčištění, můžete provést spravovaný objekt finalizovatelný. Dokončení se skládá z akce vyčištění, které jsou spuštěny při objektu je již používán. Když spravovaný objekt přestane být funkční, provede akce vyčištění, které jsou uvedeny v jeho finalizační metodě.  
  
 Při zjištění finalizovatelný objekt mrtvý, jeho finalizační metoda je umístit do fronty tak, že jsou provedeny jeho akce vyčištění, ale samotný objekt je povýšen na novou generaci. Proto budete muset počkat do dalšího uvolnění, ke které dochází v této generací (což není nutně další uvolňování) k určení, zda byl objekt uvolněn.  
  
 [Zpět na začátek](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>Uvolňování paměti pracovní stanice a serveru  
 Uvolňování je samoobslužné a může fungovat v široké škály scénářů. Soubor nastavení konfigurace můžete použít k nastavení typu uvolňování paměti kolekce založené na ukazatelích pracovního zatížení. CLR poskytuje následující typy uvolňování paměti:  
  
- Uvolnění paměti pracovní stanice, která je pro všechny pracovní stanice klienta a samostatné počítače. Toto je výchozí nastavení [ \<gcServer > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ve schématu konfigurace modulu runtime.  
  
     Uvolnění paměti pracovní stanice může být souběžné nebo nesouběžné. Souběžné uvolňování umožňuje spravovaným vláknům pokračovat v operaci během uvolňování paměti.  
  
     Od verze rozhraní .NET Framework 4, uvolňování na pozadí nahrazuje souběžné uvolňování paměti.  
  
- Uvolnění paměti serveru, který je určen pro serverové aplikace, které vyžadují vysoký výkon a škálovatelnost. Uvolnění paměti serveru může být nesouběžné nebo pozadí.  
  
 Následující ilustrace znázorňují vyhrazená vlákna, které vykonávají uvolňování paměti na serveru.  
  
 ![Vlákna uvolňování paměti serveru](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Uvolnění paměti serveru  
  
### <a name="configuring-garbage-collection"></a>Konfigurace uvolnění paměti  
 Můžete použít [ \<gcServer > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) schématu konfigurace modulu runtime pro určení typu uvolnění paměti, kterou chcete, aby modul CLR k provedení. Pokud tento prvek `enabled` atribut je nastaven na `false` (výchozí), CLR provádí uvolňování paměti pracovní stanice. Při nastavení `enabled` atribut `true`, CLR provádí uvolňování paměti serveru.  
  
 Souběžné uvolňování je vyznačeno s [ \<gcConcurrent > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) schématu konfigurace modulu runtime. Ve výchozím nastavení je `enabled`. Toto nastavení určuje, jak současných a uvolňování paměti na pozadí.  
  
 Můžete také určit uvolnění paměti serveru pomocí nespravovaných hostitelských rozhraní. Všimněte si, že technologie ASP.NET a SQL Server umožňují uvolňování paměti serveru automaticky pokud je vaše aplikace umístěna uvnitř jednoho z těchto prostředí.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>Porovnání uvolňování paměti pracovní stanice a serveru  
 Následující je práce s vlákny a posouzení výkonu pro uvolnění paměti pracovní stanice:  
  
- Kolekce probíhá u uživatele vlákna, která spouští uvolnění paměti a zůstává na stejné prioritě. Protože uživatelská vlákna obvykle běží s normální prioritou, uvolňování paměti (který se spouští ve vláknu s normální prioritou) musí soutěžit s ostatními vlákny o čas procesoru.  
  
     Vlákna, která spouští nativní kód, nejsou pozastavena.  
  
- Uvolnění paměti pracovní stanice je vždy použita v počítači, který má pouze jeden procesor, bez ohledu na to [ \<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) nastavení. Pokud zadáte uvolnění paměti serveru, používá modul CLR uvolnění paměti pracovní stanice se zakázanou souběžností.  
  
 Následující je práce s vlákny a posouzení výkonu pro uvolnění paměti serveru:  
  
- Kolekce se vyskytují ve více vyhrazených podprocesech spuštěných na `THREAD_PRIORITY_HIGHEST` úroveň priority.  
  
- Halda a vyhrazené vlákno pro provádění uvolnění paměti jsou k dispozici pro každý procesor a haldy jsou shromažďovány ve stejnou dobu. Každá halda obsahuje malou a velkou objektovou haldu, a všechny haldy lze využívat pomocí uživatelského kódu. Objekty v různých haldách mohou odkazovat na sebe navzájem.  
  
- Protože více vláken uvolňování paměti spolupracuje, uvolnění paměti serveru je rychlejší než uvolnění paměti pracovní stanice na stejnou velikostí haldy.  
  
- Uvolnění paměti serveru často zahrnuje větší velikosti segmentů. Pamatujte však, že se jedná pouze generalizace: velikost segmentu je specifický pro implementaci a můžou podléhat změnám. Měli byste zajistit žádné předpoklady o velikosti segmentů přidělaná systému uvolňování paměti při ladění aplikace.  
  
- Uvolnění paměti serveru může být náročná. Například pokud máte 12 procesů spuštěných v počítači, který má 4 procesory, bude existovat 48 vyhrazených vláken pro uvolnění se použití uvolnění paměti serveru. V situaci, načítání velkého množství paměti všechny procesy zahájí uvolnění paměti, bude mít systému uvolňování paměti naplánovat 48 vláken.  
  
 Pokud používáte stovky instancí aplikace, zvažte použití uvolňování paměti pracovní stanice se zakázaným souběžným uvolňováním. Výsledkem bude méně přepínání kontextu, což může zlepšit výkon.  
  
 [Zpět na začátek](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Souběžné uvolňování paměti  
 V procesu uvolnění paměti pracovní stanice nebo serveru můžete povolit souběžné uvolňování paměti, která umožňuje činnost vyhrazené vlákno, které provádí uvolňování paměti pro většinu doby trvání uvolňování vláken souběžně. Tato možnost se týká pouze kolekce uvolnění paměti v generaci 2; generace 0 a 1 jsou vždy nesouběžné, protože se velmi rychle dokončují.  
  
 Souběžné uvolňování umožňuje minimalizací pauzy potřebné pro kolekci se více přizpůsobovat interaktivním aplikacím. Spravovaná vlákna mohou nadále spouštět ve většině případů je spuštěn vlákno souběžné uvolňování paměti. V důsledku kratších pauz během uvolňování paměti.  
  
 Pro zvýšení výkonu při několika spuštěných procesech zakažte souběžné uvolňování paměti. Můžete to provést tak, že přidáte [ \<gcConcurrent > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do konfiguračního souboru aplikace a nastavení hodnoty jeho `enabled` atribut `"false"`.  
  
 Souběžné uvolňování paměti se provádí na vyhrazeném vlákně. Ve výchozím nastavení spustí CLR uvolnění paměti pracovní stanice s povolení souběžného uvolnění. To platí pro počítače s jedním procesorem i s více procesory.  
  
 Vaše schopnost přidělovat malé objekty v haldě během souběžného uvolňování je omezená objekty na dočasný segment při spuštění souběžné uvolňování. Jakmile dosáhnete konce segmentu, budete muset počkat souběžného uvolňování paměti na dokončení, zatímco spravovaná vlákna, která musí provést přidělení malých objektů jsou pozastavena.  
  
 Souběžné uvolňování paměti je o něco větší pracovní sadu (ve srovnání s nesouběžným uvolňování), protože můžete objekty přidělit při souběžných kolekcích. Nicméně to může ovlivnit výkon, protože objekty, které přidělíte se stanou součástí pracovní sady. Souběžné uvolňování paměti v podstatě obchoduje procesoru a paměti pro kratších pauz.  
  
 Následující obrázek znázorňuje souběžné uvolňování paměti prováděné na samostatném vyhrazeném vlákně.  
  
 ![Souběžných vláken pro uvolnění](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Souběžné uvolňování paměti  
  
 [Zpět na začátek](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Uvolnění paměti pracovní stanice na pozadí  
 V uvolňování paměti na pozadí jsou dočasné generace (0 a 1) shromažďovány podle potřeby, zatímco probíhá shromažďování generace 2. Neexistuje žádné nastavení pro uvolňování paměti na pozadí; je automaticky povoleno se souběžným uvolňováním. Uvolňování paměti na pozadí nahrazuje souběžné uvolňování paměti. Jako s souběžné uvolňování paměti, uvolňování paměti na pozadí se provádí na vyhrazeném vlákně a je použitelné pouze pro kolekce generace 2.  
  
> [!NOTE]
>  Uvolňování paměti na pozadí je k dispozici pouze v rozhraní .NET Framework 4 a novější verze. V rozhraní .NET Framework 4 je podporována pouze pro uvolnění paměti pracovní stanice. Od verze rozhraní .NET Framework 4.5, uvolňování paměti na pozadí je k dispozici pro uvolnění paměti pracovní stanice a serveru.  
  
 Kolekce na dočasných generacích během uvolňování paměti na pozadí se nazývá uvolnění paměti popředí. Pokud dojde k uvolnění paměti popředí, všechna spravovaná vlákna jsou pozastavena.  
  
 Když probíhá uvolňování paměti na pozadí a přidělili jste dost objektů v generaci 0, CLR provádí uvolňování paměti generace 1 popředí generace 0 nebo. Pozadí vyhrazené vlákno kolekce uvolnění paměti kontroluje časté bezpečné body k určení, zda je žádost o uvolnění paměti popředí. Pokud existuje, shromažďování na pozadí je pozastaveno, aby mohla probíhat kolekce paměti v popředí. Po dokončení kolekce paměti popředí, pozadí vyhrazené vlákno kolekce uvolnění paměti a uživatelská vlákna pokračovat.  
  
 Uvolňování paměti na pozadí odebere omezení přidělení stanovená souběžným uvolňováním, protože k dočasnému uvolnění může dojít během uvolňování paměti na pozadí. To znamená, že uvolňování paměti na pozadí může odstraňovat neživé v dočasných generací a může také rozšířit haldu v případě potřeby v průběhu 1 uvolnění paměti generace.  
  
Následující obrázek znázorňuje pozadí uvolňování paměti prováděné na samostatném vyhrazeném vlákně na pracovní stanici:
  
 ![Diagram zobrazující průběh uvolnění paměti pracovní stanice na pozadí.](./media/fundamentals/background-workstation-garbage-collection.png)
   
 [Zpět na začátek](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Uvolnění paměti serveru na pozadí  
 Od verze rozhraní .NET Framework 4.5, uvolňování paměti serveru na pozadí je výchozím režimem pro uvolňování paměti serveru. Zvolit tento režim, nastavte `enabled` atribut [ \<gcServer > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) k `true` ve schématu konfigurace modulu runtime. Tento režim funguje podobně k uvolnění paměti pracovní stanice na pozadí, je popsáno v předchozí části, ale existuje několik rozdílů. Uvolnění paměti pracovní stanice na pozadí používá jeden pozadí vyhrazené vlákno uvolňování paměti, zatímco uvolňování paměti serveru na pozadí používá více vláken, obvykle jedno vyhrazené vlákno pro každý logický procesor. Na rozdíl od kolekce vlákna uvolňování paměti na pozadí pracovní stanice tato vlákna nikdy nevyprší.  
  
 Následující obrázek znázorňuje pozadí uvolňování paměti prováděné na samostatném vyhrazeném vlákně na serveru:  
  
 ![Diagram zobrazující průběh uvolňování paměti serveru na pozadí.](./media/fundamentals/background-server-garbage-collection.png)  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
