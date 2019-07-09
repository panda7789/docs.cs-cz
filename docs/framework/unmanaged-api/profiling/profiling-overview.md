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
ms.openlocfilehash: 6dbf36cec1bcd2ec1e96d57a889ddd9d9baef269
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663894"
---
# <a name="profiling-overview"></a>Přehled profilace

<a name="top"></a> Profiler je nástroj, který sleduje spuštění jiné aplikace. Common language runtime (CLR) profiler je dynamická knihovna (DLL), který obsahuje funkce, které přijímají zprávy z a odesílání zpráv do CLR pomocí Profilování rozhraní API. Knihovna DLL profileru je načtena modulem CLR za běhu.

Tradiční nástroje profilování se zaměřují na měření provádění aplikace. To znamená že měří čas, který byl stráven v každé funkci nebo využití paměti aplikace v čase. Rozhraní API pro profilaci, zaměřuje na širší třídu diagnostických nástrojů, jako jsou nástroje pro průchod kódem a dokonce i pokročilé pomůcky ladění. Tato použití jsou všechna z podstaty diagnostická. Rozhraní API profilování nejen měří, ale také sleduje provádění aplikace. Z tohoto důvodu profilování rozhraní API byste nikdy neměli používat samotné aplikaci a spuštění aplikace nemělo záviset (nebo být ovlivněno) profilerem.

Profilování aplikace CLR vyžaduje větší podporu než profilování konvenčně zkompilovaného strojového kódu. Důvodem je, že modul CLR zavádí pojmy jako domény aplikace, uvolňování, spravované zpracování výjimek, just-in-time (JIT) kompilaci kódu (převod jazyka Microsoft intermediate language, nebo MSIL do nativního strojového kódu) a podobné funkce. Konvenční mechanismy profilování nelze identifikovat ani poskytnout užitečné informace o těchto funkcích. Rozhraní API profilování poskytuje tyto chybějící informace efektivně s minimálním vlivem na výkon modulu CLR a profilované aplikace.

Kompilace JIT za běhu poskytuje dobrou příležitostí pro profilování. Rozhraní profilování API umožňuje profileru změnit stream kódu v paměti MSIL pro rutinu před kompilací JIT. Tímto způsobem profiler dynamicky přidá kód instrumentace do konkrétních rutin, které vyžadují hlubší šetření. Přestože tento přístup je možný v běžných situacích, je mnohem snazší implementovat pro CLR pomocí Profilování rozhraní API.

Tento přehled obsahuje následující části:

- [Rozhraní API pro profilaci](#profiling_api)

- [Podporované funkce](#support)

- [Vlákna oznámení](#notification_threads)

- [Zabezpečení](#security)

- [Kombinace spravovaného a nespravovaného kódu v Profiler kódu](#combining_managed_unmanaged)

- [Profilování nespravovaného kódu](#unmanaged)

- [Používání modelu COM](#com)

- [Zásobníky volání](#call_stacks)

- [Zpětná volání a hloubka zásobníku](#callbacks)

- [Související témata](#related_topics)

<a name="profiling_api"></a>

## <a name="the-profiling-api"></a>Rozhraní API pro profilaci

Rozhraní API profilování se obvykle používá k zápisu *profileru kód*, což je program, který sleduje běh spravované aplikace.

Rozhraní API profilování je používáno profilerem knihovny DLL, který je zaveden ve stejném procesu jako aplikace, která je právě profilována. Knihovna DLL profileru implementuje rozhraní zpětného volání ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) v rozhraní .NET Framework verze 1.0 a 1.1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) ve verzi 2.0 a novější). CLR volá metody v tomto rozhraní pro oznámení profileru událostí PROFILOVANÉHO procesu. Profiler volat zpět do modulu runtime pomocí metod v [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) a [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) rozhraní k získání informací o stavu profilované aplikace.

> [!NOTE]
> Pouze část shromažďování dat řešení profileru by měl běžet ve stejném procesu jako profilovaná aplikace. Všechny analýzy uživatelského rozhraní a dat je třeba provést v samostatném procesu.

Následující obrázek znázorňuje interakci profileru DLL s aplikací, která je právě profilována a CLR.

![Snímek obrazovky zobrazující profilování architektury.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Rozhraní oznámení

[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) lze považovat za rozhraní upozornění. Tato rozhraní se skládají z metod, jako [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), a [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Pokaždé, když modul CLR načte nebo zruší načtení třídy, zkompiluje funkci, a tak dále, zavolá odpovídající metodu v profileru `ICorProfilerCallback` nebo `ICorProfilerCallback2` rozhraní.

Například profilování může měřit výkon kódu přes dvě funkce oznámení: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Prostě časová razítka každého oznámení, shromáždí výsledky a vypíše seznam, který určuje, které funkce spotřebované nejvíce procesoru nebo v nastavenou času během spuštění aplikace.

### <a name="the-information-retrieval-interfaces"></a>Rozhraní načítání informací

Další hlavní rozhraní součástí profilování jsou [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) a [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profiler volá tato rozhraní podle potřeby k získání dalších informací usnadňujících analýzu. Například pokaždé, když kterou volá CLR [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funkce, poskytne funkci identifikátor. Profiler můžete získat další informace o této funkci voláním [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda ke zjištění nadřazené třídy funkce, název a tak dále.

[Zpět na začátek](#top)

<a name="support"></a>

## <a name="supported-features"></a>Podporované funkce

Rozhraní API profilování poskytuje informace o různých událostech a akcích, které se vyskytují v modulu common language runtime. Tyto informace můžete použít ke sledování vnitřního chodu procesů a k analýze výkonu aplikace .NET Framework.

Rozhraní API profilování načítá informace o následujících akcích a událostech, které se vyskytují v CLR:

- Události spuštění a vypnutí CLR.

- Aplikace domain událost vytvoření a ukončení.

- Načítání a uvolňování události sestavení.

- Modul události načítání a uvolňování.

- Vytváření a ničení událostí serveru COM vtable.

- Just-in-time (JIT) kompilaci a události odsazování kódu.

- Události načítání a uvolňování třídy.

- Události vytváření a ničení vlákna.

- Vstupní a výstupní události funkce.

- Výjimky.

- Přechody mezi spravovaným a nespravovaným kódem provádění.

- Přechody mezi různými kontexty za běhu.

- Informace o pozastavení běhu.

- Informace o modulu runtime paměti haldy a uvolňování paměti kolekce aktivity.

Rozhraní API profilování lze volat z libovolného (nespravovaného) jazyka kompatibilního s modelem COM.

Rozhraní API je efektivní z hlediska spotřeby procesoru a paměti. Profilování nezahrnuje změny profilované aplikace, které jsou natolik závažné, aby způsobovaly zavádějící výsledky.

Rozhraní API profilování je užitečné pro vzorkovací i nevzorkovací profilovací programy. A *vzorkování profileru* kontroluje profil při pravidelných taktech, například 5 milisekund od sebe. A *profiler bez vzorkování* je informován o události synchronně s vláknem, které událost způsobilo.

### <a name="unsupported-functionality"></a>Nepodporované funkce

Rozhraní profilování API nepodporuje následující funkce:

- Nespravovaný kód, který musí být profilován použitím konvenčních metod Win32. Profiler modulu CLR však zahrnuje události přechodu k určení hranic mezi spravovaným a nespravovaným kódem.

- Aplikace, které upravují vlastní kód pro účely, jako je aspektově orientované programování upravující samy sebe.

- Kontrola hranic, protože profilování rozhraní API neposkytuje tyto informace. CLR poskytuje vnitřní podporu pro kontrolu veškerého spravovaného kódu hranic.

- Vzdálené profilování, což není podporováno z následujících důvodů:

  - Vzdálené profilování prodlužuje dobu provádění. Při použití rozhraní profilování musíte minimalizovat čas spuštění, aby výsledky profilování nepřiměřeně ovlivněny. To platí zejména při sledování výkonu provádění. Ale vzdálené profilování není omezení při rozhraní profilování se používají ke sledování využití paměti nebo k získání informací o rámce zásobníku, objekty a tak dále.

  - Profiler kódu CLR musí zaregistrovat jedno nebo více rozhraní zpětného volání s modulem runtime v místním počítači, na kterém je spuštěný profilované aplikace. To omezuje schopnost vytvářet profiler vzdáleného kódu.

- Profilování v provozním prostředí s požadavky na vysokou dostupnost. Rozhraní API profilování bylo vytvořeno pro podporu diagnostiky v době vývoje. Nebylo podrobeno, přísnému testování potřebnému pro podporu výrobních prostředí.

[Zpět na začátek](#top)

<a name="notification_threads"></a>

## <a name="notification-threads"></a>Vlákna oznámení

Ve většině případů vlákno, které generuje událost spustí oznámení. Taková oznámení (například [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) a [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) nemusí poskytovat explicitní `ThreadID`. Také profiler může rozhodnout použít místní úložiště vláken k ukládání a aktualizaci bloků analýzy namísto indexování bloků analýzy v globálním úložišti, na základě `ThreadID` ovlivněného vlákna.

Všimněte si, že tato zpětná volání nejsou serializována. Uživatelé musí chránit svůj kód vytvořením vláknově bezpečných datových struktur a uzamčením kódu profileru v případě potřeby k zabránění paralelního přístupu z více vláken. Proto v některých případech je možné přijímat neobvyklou sekvenci zpětných volání. Předpokládejme například, že spravovaná aplikace vyvolává dvě vlákna, která spouští stejný kód. V takovém případě je možné přijímat [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) událost pro některé funkce z jednoho podprocesu a `FunctionEnter` zpětného volání z jiného podprocesu před přijetím [ ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) zpětného volání. V tomto případě uživatel obdrží `FunctionEnter` zpětné volání pro funkci, která pravděpodobně ještě nebyla plně just-in-time (JIT) zkompilována.

[Zpět na začátek](#top)

<a name="security"></a>

## <a name="security"></a>Zabezpečení

Profiler DLL je nespravovaná knihovna DLL, která se spouští jako součást common language runtime prováděcí modul. V důsledku toho kód v profileru DLL není v souladu s omezením zabezpečení přístupu spravovaného kódu. Jediná omezení profileru knihoven DLL jsou ta uvalená operační systém na uživatele, který se spouští profilovanou aplikaci.

Autoři Profiler by měl přijmout vhodná opatření k zamezení problémů souvisejících se zabezpečením. Například během instalace, knihovna DLL profileru by měl přidat na seznam řízení přístupu (ACL) tak, aby ho nemohli měnit uživatel se zlými úmysly.

[Zpět na začátek](#top)

<a name="combining_managed_unmanaged"></a>

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Kombinace spravovaného a nespravovaného kódu v Profiler kódu

Chybně napsaný profiler může způsobit cyklické odkazy na sebe sama, v důsledku nepředvídatelného chování.

Přehled rozhraní API profilování CLR může vytvořit dojem, že píšete profiler, který obsahuje spravované a nespravované součásti, které volají navzájem prostřednictvím volání spolupráce nebo nepřímých COM.

I když je to možné z hlediska návrhu, nepodporuje profilování rozhraní API spravované součásti. CLR profiler musí být zcela nespravovaný. Pokusy spojit v profileru CLR spravovaný a nespravovaný kód mohou způsobit narušení přístupu, selhání program nebo zablokování. Spravované součásti profileru vrátí události zpět nespravovaným součástem, které následně zavolal spravované součásti, výsledkem jsou cyklické odkazy.

Je jediným umístěním, kde CLR profiler může volat spravovaný kód bezpečně v těle Microsoft intermediate language (MSIL) metody. Doporučený postup pro úpravu textu jazyka MSIL je použít metody rekompilace JIT v [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní.

Je také možné použít starší metody instrumentace ke změně jazyka MSIL. Před dokončením kompilace just-in-time (JIT) funkce může profiler vložit spravovaná volání do těla MSIL metody a poté ji JIT-kompilovat ji (viz [ICorProfilerInfo::GetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) metoda). Tato technika lze úspěšně použít pro selektivní instrumentaci spravovaného kódu nebo ke shromáždění dat statistiky a výkonu o JIT.

Alternativně může profiler kódu vložit nativní háky do těla MSIL každé spravované funkce, která volá nespravovaný kód. Tento postup můžete použít pro instrumentaci a pokrytí. Například profiler kódu může vložit háky instrumentace za každý blok MSIL k zajištění, že blok byl proveden. Modifikace těla MSIL metody je velmi Jemná operace a existuje celá řada faktorů, které by měl brát v úvahu.

[Zpět na začátek](#top)

<a name="unmanaged"></a>

## <a name="profiling-unmanaged-code"></a>Profilování nespravovaného kódu

Common language runtime (CLR) rozhraní API profilování poskytuje minimální podporu pro profilování nespravovaného kódu. Je k dispozici následující funkce:

- Výčet řetězů zásobníku. Tato funkce umožňuje profileru kódu stanovit hranici mezi spravovaným kódem a nespravovaným kódem.

- Určení, zda řetěz zásobníku odpovídá spravovanému kódu nebo nativním kódu.

V rozhraní .NET Framework verze 1.0 a 1.1 tyto metody jsou k dispozici prostřednictvím podmnožinu API ladění CLR v procesu. Jsou definovány v souboru CorDebug.idl.

V rozhraní .NET Framework 2.0 nebo novější, můžete použít [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodu pro tuto funkci.

[Zpět na začátek](#top)

<a name="com"></a>

## <a name="using-com"></a>Používání modelu COM

Přestože rozhraní profilování jsou definována jako rozhraní modelu COM, modul CLR (CLR) skutečně neinicializuje COM k použití těchto rozhraní. Důvodem je, abyste se vyhnuli nutnosti nastavit model vláken pomocí [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) funkce předtím, než spravovaná aplikace dostala příležitost k určení požadovaného modelu vlákna. Podobně, profiler samotný neměl volat `CoInitialize`, protože může vybrat model vlákna, která není kompatibilní s profilovanou aplikací a může způsobit selhání aplikace.

[Zpět na začátek](#top)

<a name="call_stacks"></a>

## <a name="call-stacks"></a>Zásobníky volání

Rozhraní API profilování poskytuje dva způsoby, jak získat zásobníky volání: metodu snímku zásobníku, umožňující řídké shromažďování zásobníků volání a metodu stínového zásobníku, která sleduje zásobník volání v každém okamžiku.

### <a name="stack-snapshot"></a>Snímek zásobníku

Snímek zásobníku je trasování zásobníku vlákna v okamžiku v čase. Rozhraní API profilování podporuje trasování spravovaných funkcí v zásobníku, ale ponechává trasování nespravovaných funkcí na zásobníkem profileru vlastní.

Další informace o tom, jak programovat profiler, aby procházel spravované zásobníky, najdete v článku [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody v této sadě dokumentace a [Profiler procházení zásobníku v rozhraní .NET Framework 2.0: Základy i mimo ně](https://go.microsoft.com/fwlink/?LinkId=73638).

### <a name="shadow-stack"></a>Stínový zásobník

Příliš časté používání metody snímku může rychle vytvořit potíže s výkonem. Pokud chcete často přebírat trasování zásobníku, váš profiler by měl místo toho vytvořit stín zásobníku pomocí [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) zpětných volání výjimky. Stínový zásobník je vždy aktuální a lze ho snadno zkopírovat do úložiště vždy, když je potřeba snímek zásobníku.

Stínový zásobník může získat argumenty funkce, vrácené hodnoty a informace o obecných instancích. Tyto informace jsou k dispozici pouze prostřednictvím stínového zásobníku a mohou být získány při předání řízení funkci. Tyto informace však nemusí být k dispozici později při spuštění funkce.

[Zpět na začátek](#top)

<a name="callbacks"></a>

## <a name="callbacks-and-stack-depth"></a>Zpětná volání a hloubka zásobníku

Zpětná volání Profiler mohou být vydána při velmi omezeném zásobníku a přetečení zásobníku při zpětném volání profileru povede k okamžitému ukončení procesu. Profiler by měl Ujistěte se, že použije co nejmenší zásobník v reakci na zpětná volání. Pokud profiler je určen pro použití s procesy, které jsou odolnější proti přetečení zásobníku, profiler sám by také se vyhnout neměl spouštět přetečení zásobníku.

[Zpět na začátek](#top)

<a name="related_topics"></a>

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Nastavení prostředí profilace](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Vysvětluje, jak inicializovat profilování, nastavit oznámení událostí a Profilovat službu Windows.|
|[Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Popisuje nespravovaná rozhraní, které používá profilování API.|
|[Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Popisuje nespravované globální statické funkce, které používá profilování API.|
|[Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Popisuje nespravované výčty, které používá profilování API.|
|[Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Popisuje nespravované struktury, které používá profilování API.|
