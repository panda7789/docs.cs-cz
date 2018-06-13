---
title: Přehled profilace
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b38b64e1c86174bea11086e722ed86b0a0046e2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461910"
---
# <a name="profiling-overview"></a>Přehled profilace
<a name="top"></a> Profileru je nástroj, který monitoruje provádění jiná aplikace. Běžné profileru language runtime (CLR) je dynamická knihovna (DLL), která se skládá z funkcí, které příjem zpráv z a odeslání zpráv do modulu CLR pomocí rozhraní API pro profilaci. Profileru knihovnu DLL modulu CLR zavedená v době běhu.  
  
 Tradiční nástroje pro profilaci zaměřit se na měření spuštění aplikace. To znamená že měření času stráveného v každé funkce nebo využití paměti aplikace v průběhu času. Profilace API cílí širší třídu diagnostických nástrojů, jako jsou nástroje pro pokrytí kódu a i rozšířené ladění pomůcky. Tato použití jsou všechny diagnostiky ve své podstatě. Profilace API nejen měří, ale také monitoruje spuštění aplikace. Z tohoto důvodu profilaci API by nikdy používat vlastní aplikace a spuštění aplikace by neměl závisí na (nebo mít vliv) profileru.  
  
 Profilace aplikace CLR vyžaduje další podporu než profilace obvykle zkompilovaný kód počítače. Důvodem je, že modulu CLR seznámíte se základními pojmy, jako je aplikační domény, uvolňování paměti, spravované zpracování výjimek v běhu (JIT) kompilace kódu (Převod Microsoft převodní jazyk nebo MSIL kódu do nativního kódu počítače) a podobných funkce. Konvenční profilování mechanismy nelze identifikovat nebo poskytují užitečné informace o těchto funkcích. Profilace API poskytuje tyto chybějící informace efektivně minimální vliv na výkon modulu CLR a PROFILOVANÉHO aplikace.  
  
 JIT – kompilace v době běhu poskytuje dobrý příležitosti pro profilace. Profilace API umožňuje profileru změnit datový proud MSIL kód v paměti pro rutinu, která předtím, než je kompilována. Tímto způsobem můžete profileru dynamicky přidat kód instrumentace na konkrétní rutiny, které je třeba hlubší rozbor. I když tento přístup je možné v běžné scénáře, je mnohem snazší implementací pro modulu CLR pomocí rozhraní API pro profilaci.  
  
 Tento přehled se skládá z následujících částí:  
  
-   [Rozhraní API pro profilaci](#profiling_api)  
  
-   [Podporované funkce](#support)  
  
-   [Vlákna oznámení](#notification_threads)  
  
-   [Zabezpečení](#security)  
  
-   [Kombinování spravovaných a nespravovaných kód v kódu profileru](#combining_managed_unmanaged)  
  
-   [Profilace nespravovaného kódu](#unmanaged)  
  
-   [Pomocí modelu COM](#com)  
  
-   [Zásobníky volání](#call_stacks)  
  
-   [Zpětná volání a hloubka zásobníku](#callbacks)  
  
-   [Související témata](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>Rozhraní API pro profilaci  
 Obvykle profilaci API slouží k zápisu *code profileru*, což je program, který monitoruje spuštění spravované aplikace.  
  
 Profilace API používá profileru knihovny DLL, který je načten do stejně jako aplikace, která je profilovaný. Profileru DLL implementuje rozhraní pro zpětné volání ([icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) v rozhraní .NET Framework verze 1.0 a 1.1, [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) ve verzi 2.0 nebo novější). Modul CLR volá metody v tomto rozhraní oznámit profileru událostí v PROFILOVANÉHO procesu. Profileru můžete volat zpět do modulu runtime podle pomocí metody v [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) a [ICorProfilerInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) rozhraní, které se získat informace o stavu PROFILOVANÉHO aplikace.  
  
> [!NOTE]
>  Jenom tu část shromažďování dat profileru řešení by měl být spuštěn v rámci jednoho procesu jako PROFILOVANÉHO aplikace. Všechny uživatelské rozhraní a data se analyzují jako samostatný proces.  
  
 Následující obrázek znázorňuje interakci profileru DLL se aplikace, která je profilovaný a modulu CLR.  
  
 ![Profilace architektura](../../../../docs/framework/unmanaged-api/profiling/media/profilingarch.png "ProfilingArch")  
Architektura profilace  
  
### <a name="the-notification-interfaces"></a>Rozhraní oznámení  
 [Icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) lze považovat za rozhraní oznámení. Tato rozhraní se skládají z metod, jako [classloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [classloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), a [jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Pokaždé, když načtení modulu CLR nebo opuštění třídu, zkompiluje funkce, a atd., volá metodu odpovídající v okna profilování `ICorProfilerCallback` nebo `ICorProfilerCallback2` rozhraní.  
  
 Například může profileru měření výkonu kód prostřednictvím dvě funkce oznámení: [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) a [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Ji jenom časová razítka každého oznámení shromažďuje výsledky a vypíše seznam, která určuje, které funkce použít nejvíce procesoru nebo wall hodiny času při spuštění aplikace.  
  
### <a name="the-information-retrieval-interfaces"></a>Načítání informací o rozhraní  
 Další zahrnutých v profilaci hlavní rozhraní jsou [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) a [ICorProfilerInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profileru zavolá tato rozhraní podle potřeby získat další informace, které pomohou jeho analýzu. Vždy, když modul CLR například volá [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funkce, poskytne identifikátor funkce. Profileru můžete získat další informace o této funkci voláním [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda zjišťování funkce nadřazené třídy, jeho název a tak dále.  
  
 [Zpět na začátek](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Podporované funkce  
 Profilace API poskytuje informace o různých události a akce, ke kterým došlo v modulu CLR. Tyto informace můžete použít ke sledování vnitřního chodu procesy a analýza výkonu aplikace .NET Framework.  
  
 Profilace API načte informace o následující akce a události, ke kterým došlo v modulu CLR:  
  
-   Události spuštění a vypnutí CLR.  
  
-   Vytváření a vypnutí události serveru aplikace domény.  
  
-   Sestavení načítání a uvolňování události.  
  
-   Modul načítání a uvolňování události.  
  
-   Vytváření a likvidace události serveru COM vtable.  
  
-   V běhu (JIT) kompilace a kód pitching události.  
  
-   Třídy událostí načtení a odinstalování.  
  
-   Vytváření a likvidace události vláken.  
  
-   Funkce vstupní a výstupní události.  
  
-   Výjimky.  
  
-   Přechodů mezi spravovanými a nespravovanými kód provádění.  
  
-   Přechodů mezi kontexty jiný modul runtime.  
  
-   Informace o pozastavení modulu runtime.  
  
-   Informace o modulu runtime paměti haldy a uvolňování paměti kolekce aktivity.  
  
 Profilaci API je možné volat z jakéhokoli jazyka kompatibilní COM (nespravované).  
  
 Rozhraní API je efektivní s ohledem na spotřeby procesoru a paměti. Profilace nezahrnuje změny PROFILOVANÉHO aplikace, které důležité, aby zavádějící výsledky.  
  
 Profilace API je užitečné profilery vzorkování i bez vzorkování. A *vzorkování profileru* zkontroluje profilu v pravidelných počtu taktů Řekněme, na 5 milisekund od sebe. A *bez vzorkování profileru* informován o událost synchronně vlákno, které způsobí, že událost.  
  
### <a name="unsupported-functionality"></a>Nepodporované funkce  
 Profilace API nepodporuje následující funkce:  
  
-   Nespravovaný kód, který musí být profilovaným konvenční metodami Win32. Profileru CLR však obsahuje přechod událostí k určení hranice mezi spravovanými a nespravovanými kódu.  
  
-   Samoobslužné úpravy aplikací, které upravit vlastní kód pro účely, například aspekt orientované programování.  
  
-   Rozsah kontroly, protože profilaci API neposkytuje tyto informace. Modul CLR poskytuje vnitřní podporu pro rozsah kontroluje všechny spravovaného kódu.  
  
-   Vzdálené profilování, což není podporováno z následujících důvodů:  
  
    -   Čas spuštění vzdáleného profilování rozšiřuje. Při použití rozhraní profilace musí se tak, aby profilace výsledky nebude mít vliv neoprávněně minimalizovat dobu provádění. To platí hlavně při provádění výkonu je monitorována. Ale vzdálené profilování není omezení při profilování rozhraní se používají k monitorování využití paměti, nebo se získat informace o běhu o rámce zásobníku, objekty a tak dále.  
  
    -   Kód profileru CLR musí zaregistrovat jedno nebo více rozhraní zpětné volání s modulem runtime v místním počítači, na kterém je spuštěný PROFILOVANÉHO aplikace. Toto nastavení omezuje schopnost vytvářet profileru vzdáleného kódu.  
  
-   Profilace v produkčním prostředí s vysokou dostupností požadavky. Profilace API byl vytvořen pro podporu vývoj čas diagnostiky. Neprošel přísných testování potřebné k podpoře provozní prostředí.  
  
 [Zpět na začátek](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Vlákna oznámení  
 Ve většině případů podproces, který vygeneruje událost, také provede oznámení. Tato oznámení (například [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) a [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) není potřeba zadat explicitní `ThreadID`. Navíc profileru rozhodnout pro ukládání a aktualizujte jeho analysis bloků místo indexování analysis bloky v globální úložiště, na základě používat úložiště thread-local `ThreadID` ovlivněných vlákna.  
  
 Všimněte si, že nejsou serializované tyto zpětných volání. Uživatelé musí chránit svůj kód tak, že vytvoříte bezpečné pro přístup z více vláken datové struktury a blokováním kód profileru tam, kde je to nutné zabránit paralelní přístup z více vláken. Proto v některých případech může přijímat neobvyklou posloupnost zpětných volání. Předpokládejme například, že spravované aplikace je například dvě vláken, které jsou prováděny identické kódu. V takovém případě je možné přijímat [icorprofilercallback::jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) událost pro některé funkce z jednoho vlákna a `FunctionEnter` zpětného volání z jiné vlákno před přijetím [ Icorprofilercallback::jitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) zpětného volání. V takovém případě uživatel obdrží `FunctionEnter` zpětné volání pro funkci, která nemusí být plně v běhu (JIT) ještě zkompilovat.  
  
 [Zpět na začátek](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Zabezpečení  
 Profileru DLL je nespravované knihovnu DLL, kterou spouští jako součást běžné spouštěcí modul runtime jazyka. Kód v profileru DLL není podléhá omezením uvedeným v důsledku toho spravovat zabezpečení přístupu kódu. Jediná dvě omezení u profileru DLL jsou způsobené operační systém na uživatele, který je spuštěna PROFILOVANÉHO aplikace.  
  
 Autoři profileru zabere vhodná bezpečnostní opatření, aby se zabránilo problémy související se zabezpečením. Například během instalace, profileru knihovny DLL musí být přidaní do seznam řízení přístupu (ACL) tak, aby uživatel se zlými úmysly ho nelze změnit.  
  
 [Zpět na začátek](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Kombinování spravovaných a nespravovaných kód v kódu profileru  
 Nesprávně napsaný profileru může způsobit cyklické odkazy na sebe, což vede k nepředvídatelné chování.  
  
 O rozhraní API pro profilaci modulu CLR může vytvořit dojem, že napíšete profileru, který obsahuje spravovanými a nespravovanými součásti, které volají navzájem pomocí zprostředkovatele komunikace s objekty nebo nepřímý volání COM.  
  
 I když to je možné z hlediska návrhu, profilaci API nepodporuje spravované součásti. Profileru CLR musí být zcela nespravované. Pokusy o kombinovat spravovanými a nespravovanými kód v profileru CLR může způsobit narušení přístupu, program selhání nebo zablokování. Spravované součásti profileru bude platit události zpět na nespravované součásti, které by následně volání spravované součásti znovu, což vede k cyklické odkazy.  
  
 V těle Microsoft (MSIL intermediate language) metody je jediným umístěním, kde CLR profileru můžete volat spravovaného kódu bezpečně. Doporučený postup pro úpravy textu MSIL je použít metody rekompilace JIT v [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní.  
  
 Je také možné použít k úpravě MSIL starší metody instrumentace. Před dokončením kompilace v běhu (JIT) funkce profileru můžete vložit spravované volání v těle MSIL metoda a pak JIT – kompilace ho (viz [icorprofilerinfo::getilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) metoda). Tento postup můžete použít úspěšně pro selektivní instrumentace spravovaného kódu nebo ke shromažďování statistik a výkonu dat o JIT.  
  
 Alternativně můžete vložit kód profileru nativní háky v těle MSIL každých spravované funkce, který volá nespravovaný kód. Tento postup můžete použít pro instrumentace a pokrytí. Například může profileru kód vložte instrumentace háky po každých MSIL bloku, aby provedl bloku. Úpravy textu MSIL metodu je velmi citlivé operace a existuje celá řada faktorů, které musí vzít v úvahu.  
  
 [Zpět na začátek](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Profilace nespravovaného kódu  
 Modul CLR (CLR) rozhraní API pro profilaci poskytuje minimální podporu pro profilace nespravovaného kódu. Je k dispozici následující funkce:  
  
-   Výčet řetězy zásobníku. Tato funkce umožňuje profileru kódu k určení hranice mezi spravovaného kódu a nespravovaného kódu.  
  
-   Stanovení jestli odpovídá řetězci zásobníku spravovaného kódu nebo nativního kódu.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1 tyto metody jsou k dispozici prostřednictvím v procesu podmnožinu rozhraní API pro ladění modulu CLR. Jsou definovány v souboru CorDebug.idl.  
  
 V rozhraní .NET Framework 2.0 nebo novější, můžete použít [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodu pro tuto funkci.  
  
 [Zpět na začátek](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>Pomocí modelu COM  
 I když rozhraní profilace jsou definovány jako rozhraní modelu COM, modul CLR (CLR) neinicializuje ve skutečnosti COM k použití těchto rozhraní. Důvodem je, abyste vyloučili, že nastavení modelu vláken pomocí [funkce CoInitialize](http://msdn.microsoft.com/library/windows/desktop/ms678543\(v=vs.85\).aspx) funkce před spravované aplikaci dostal příležitost k určení jeho požadované model vláken. Podobně, by neměla volat profileru samotné `CoInitialize`, protože může vybrat model vláken, který není kompatibilní s aplikací profilovaný a může způsobit selhání aplikace.  
  
 [Zpět na začátek](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Zásobníky volání  
 Profilace API poskytuje dva způsoby, jak získat zásobníky volání: metoda snímku zásobníku, umožňující zhuštěných shromažďování zásobníky volání a metoda stínové zásobníku, která sleduje zásobníku volání v každé rychlých.  
  
### <a name="stack-snapshot"></a>Snímky zásobníku  
 Snímek zásobníku je trasování zásobníku vlákna na okamžik v čase. Profilování rozhraní API podporuje trasování spravované funkce v zásobníku, ale ponechá ji trasování nespravovaných funkcí k walkera zásobníku profileru na vlastní.  
  
 Další informace o tom, jak program profileru vás spravované zásobníky najdete v tématu [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoda v této dokumentaci, a [profileru zásobníku proti v rozhraní .NET Framework 2.0: Základní informace a kromě](http://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Stínové zásobníku  
 Pomocí metody snímku příliš často můžete rychle vytvořit problém výkonu. Pokud budete chtít využít trasování zásobníku často, vaše profileru má místo sestavit stínové zásobníku pomocí [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), a [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) zpětná volání výjimek. Zásobník stínové je vždy aktuální a lze rychle zkopírovat do úložiště vždy, když je potřeba snímku zásobníku.  
  
 Zásobník stínové může získat argumenty funkce, návratové hodnoty a informace o obecné konkretizací. Tyto informace je k dispozici pouze prostřednictvím stínové zásobníku a může být získán při řízení je předat funkci. Tyto informace však nemusí být k dispozici novější během spuštění funkce.  
  
 [Zpět na začátek](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Zpětná volání a hloubka zásobníku  
 Ve velmi omezené zásobníku okolností může být vydaný profileru zpětná volání a k přetečení zásobníku v zpětné volání profileru povede k ukončení procesu okamžitě. Profileru měli používat jako málo zásobníku nejblíže v reakci na zpětných volání. Pokud profileru je určený pro použití s procesy, které jsou odolnější proti přetečení zásobníku, profileru samotné také Vyhněte se aktivuje přetečení zásobníku.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Nastavení prostředí profilace](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Vysvětluje, jak k inicializaci profileru, nastavení oznámení událostí a profilu služby systému Windows.|  
|[Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Popisuje nespravované rozhraní, která používá profilaci API.|  
|[Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Popisuje nespravované globální statické funkce, které používá profilaci API.|  
|[Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Popisuje nespravovaná vyčíslení, které používá profilaci API.|  
|[Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Popisuje nespravované struktury, které používá profilaci API.|
