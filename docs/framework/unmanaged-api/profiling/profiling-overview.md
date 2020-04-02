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
ms.openlocfilehash: 3836b562d969726a6587d702d3edf45abb147d10
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588509"
---
# <a name="profiling-overview"></a>Přehled profilace

Profiler je nástroj, který monitoruje provádění jiné aplikace. Profilování clr (Common Language runtime) je knihovna dynamických odkazů (DLL), která se skládá z funkcí, které přijímají zprávy z CLR a odesílají do ní pomocí rozhraní API profilování. DLL profileru je načten clr za běhu.

Tradiční profilovací nástroje se zaměřují na měření provádění aplikace. To znamená, že měří čas strávený v každé funkci nebo využití paměti aplikace v průběhu času. Profilování rozhraní API se zaměřuje na širší třídu diagnostických nástrojů, jako jsou nástroje pro pokrytí kódu a dokonce i pokročilé ladicí pomůcky. Tato použití jsou všechny diagnostické povahy. Profilování rozhraní API nejen měří, ale také monitoruje provádění aplikace. Z tohoto důvodu profilování rozhraní API by nikdy použít samotné aplikace a spuštění aplikace by neměla záviset na (nebo být ovlivněny) profiler.

Profilování aplikace CLR vyžaduje více podpory než profilování konvenčně kompilovaného strojového kódu. Důvodem je, že CLR zavádí koncepty, jako jsou aplikační domény, uvolňování paměti, spravované zpracování výjimek, kompilace kódu just-in-time (JIT) (převod zprostředkujícího jazyka Microsoft u MSIL nebo kódu MSIL na nativní strojový kód) a podobné funkce. Konvenční profilovací mechanismy nelze identifikovat nebo poskytnout užitečné informace o těchto funkcích. Profilování rozhraní API poskytuje tyto chybějící informace efektivně, s minimálním dopadem na výkon CLR a profilované aplikace.

Kompilace JIT za běhu poskytuje dobré příležitosti pro profilování. Profilování rozhraní API umožňuje profiler změnit datový proud kódu MSIL v paměti pro rutinu před je jit kompilované. Tímto způsobem profiler můžete dynamicky přidat kód instrumentace pro konkrétní rutiny, které potřebují hlubší šetření. I když tento přístup je možné v konvenčních scénářích, je mnohem jednodušší implementovat pro CLR pomocí profilování rozhraní API.

## <a name="the-profiling-api"></a>Rozhraní API profilování

Profilování rozhraní API se obvykle používá k napsání *profileru kódu*, což je program, který monitoruje provádění spravované aplikace.

Profilování rozhraní API používá dll profiler, který je načten do stejného procesu jako aplikace, která je profilována. Knihovna DLL profileru implementuje rozhraní zpětného volání[(ICorProfilerCallback](icorprofilercallback-interface.md) v rozhraní .NET Framework verze 1.0 a 1.1, [ICorProfilerCallback2](icorprofilercallback2-interface.md) ve verzi 2.0 a novější). CLR volá metody v tomto rozhraní upozornit profiler událostí v procesu profilované. Profiler můžete volat zpět do modulu runtime pomocí metod v [rozhraníI ICorProfilerInfo](icorprofilerinfo-interface.md) a [ICorProfilerInfo2](icorprofilerinfo2-interface.md) získat informace o stavu profilované aplikace.

> [!NOTE]
> Pouze část shromažďování dat řešení profileru by měla být spuštěna ve stejném procesu jako profilované aplikace. Všechna uživatelská rozhraní a analýza dat by měly být prováděny v samostatném procesu.

Následující obrázek znázorňuje, jak dll profileru spolupracuje s aplikací, která je profilována a CLR.

![Snímek obrazovky, který zobrazuje architekturu profilování.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Rozhraní oznámení

[ICorProfilerCallback](icorprofilercallback-interface.md) a [ICorProfilerCallback2](icorprofilercallback2-interface.md) lze považovat za rozhraní oznámení. Tato rozhraní se skládají z metod [classloadstarted](icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)a [JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md). Pokaždé, když CLR načte nebo uvolní třídu, zkompiluje funkci a tak dále, volá odpovídající metodu v profileru `ICorProfilerCallback` nebo `ICorProfilerCallback2` rozhraní.

Profiler může například měřit výkon kódu prostřednictvím dvou funkcí oznámení: [FunctionEnter2](functionenter2-function.md) a [FunctionLeave2](functionleave2-function.md). Je to jen čas-razítka každé oznámení, shromažďuje výsledky a výstupy seznam, který označuje, které funkce spotřebované nejvíce procesoru nebo nástěnné hodiny čas během provádění aplikace.

### <a name="the-information-retrieval-interfaces"></a>Rozhraní pro načítání informací

Další hlavní rozhraní podílející se na profilování jsou [ICorProfilerInfo](icorprofilerinfo-interface.md) a [ICorProfilerInfo2](icorprofilerinfo2-interface.md). Profiler volá tato rozhraní podle potřeby získat další informace, které pomohou jeho analýzu. Například vždy, když CLR volá funkci [FunctionEnter2,](functionenter2-function.md) poskytuje identifikátor funkce. Profiler můžete získat další informace o této funkci voláním [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) metoda zjistit nadřazené třídy funkce, její název a tak dále.

## <a name="supported-features"></a>Podporované funkce

Profilování rozhraní API poskytuje informace o různých událostí a akcí, ke kterým dochází v běžném jazyku runtime. Tyto informace můžete použít ke sledování vnitřního fungování procesů a k analýze výkonu aplikace rozhraní .NET Framework.

Profilování rozhraní API načte informace o následujících akcích a událostech, ke kterým dochází v CLR:

- Události spuštění a vypnutí CLR.

- Události vytvoření a vypnutí domény aplikace.

- Události načítání a vykládky sestavení.

- Události načítání a vykládky modulu.

- Com vtable vytváření a zničení události.

- Kompilace just-in-time (JIT) a události pro pitching kódu.

- Události načítání a vykládky třídy.

- Události vytváření a zničení vlákna.

- Události vstupu a ukončení funkce.

- Výjimky.

- Přechody mezi spravovaným a nespravovaným spuštěním kódu.

- Přechody mezi různými kontexty za běhu.

- Informace o pozastavení běhu.

- Informace o haldě paměti za běhu a aktivity uvolňování paměti.

Profilování rozhraní API lze volat z libovolného (nespravovaného) jazyka kompatibilního s com.

Rozhraní API je efektivní s ohledem na spotřebu procesoru a paměti. Profilování nezahrnuje změny profilované aplikace, které jsou dostatečně významné, aby způsobit zavádějící výsledky.

Profilování rozhraní API je užitečné pro vzorkování i vzorkování profilování. Vzorkovací *profiler* kontroluje profil při pravidelných hodinách, řekněme při odstupu 5 milisekund. *Profiler bez vzorkování* je informován o události synchronně s podprocesem, který způsobuje událost.

### <a name="unsupported-functionality"></a>Nepodporované funkce

Profilování rozhraní API nepodporuje následující funkce:

- Nespravovaný kód, který musí být profilován pomocí konvenčních metod Win32. Profiler CLR však zahrnuje události přechodu k určení hranic mezi spravovaným a nespravovaným kódem.

- Samomodifikující aplikace, které upravují svůj vlastní kód pro účely, jako je programování orientované na aspekt.

- Hranice kontroly, protože profilování rozhraní API neposkytuje tyto informace. CLR poskytuje vnitřní podporu pro kontrolu hranic všech spravovaných kódů.

- Vzdálené profilování, které není podporováno z následujících důvodů:

  - Vzdálené profilování prodlužuje dobu provádění. Při použití rozhraní profilování je nutné minimalizovat dobu provádění, aby výsledky profilování nebyly nepřiměřeně ovlivněny. To platí zejména při sledování výkonu spuštění. Vzdálené profilování však není omezení, pokud se rozhraní profilování používají ke sledování využití paměti nebo k získání informací za běhu o rámcích zásobníku, objektech a tak dále.

  - Profiler kódu CLR musí zaregistrovat jedno nebo více rozhraní zpětného volání s modulem runtime v místním počítači, ve kterém je spuštěna profilovaná aplikace. To omezuje možnost vytvořit vzdálený kód profiler.

## <a name="notification-threads"></a>Vlákna oznámení

Ve většině případů vlákno, které generuje událost také provede oznámení. Taková oznámení (například [FunctionEnter](functionenter-function.md) a [FunctionLeave](functionleave-function.md)) nemusí `ThreadID`poskytovat explicitní . Profiler se také může rozhodnout použít místní úložiště podprocesu k ukládání a aktualizaci jeho bloků `ThreadID` analýzy namísto indexování bloků analýzy v globálním úložišti na základě ovlivněného vlákna.

Všimněte si, že tato zpětná volání nejsou serializovány. Uživatelé musí chránit svůj kód vytvořením datových struktur bezpečných pro přístup z více vláken a uzamčením kódu profileru, pokud je to nutné, aby se zabránilo paralelnímu přístupu z více vláken. Proto v některých případech můžete přijímat neobvyklé posloupnosti zpětná volání. Předpokládejme například, že spravovaná aplikace vytváří dvě vlákna, která provádějí stejný kód. V tomto případě je možné přijmout [iCorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) událost pro některé `FunctionEnter` funkce z jednoho vlákna a zpětné volání z druhého vlákna před přijetím [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) zpětné volání. V takovém případě uživatel obdrží `FunctionEnter` zpětné volání pro funkci, která nemusí být plně just-in-time (JIT) zkompilována ještě.

## <a name="security"></a>Zabezpečení

DLL profileru je nespravovaná dll, která běží jako součást modulu provádění modulu pro spuštění modulu za běhu běžného jazyka. V důsledku toho kód v dll profiler nepodléhá omezení zabezpečení přístupu ke spravovanému kódu. Pouze omezení na dll profiler jsou ty, které jsou uloženy operační systém na uživatele, který je spuštěn profilované aplikace.

Autoři profileru by měli přijmout vhodná opatření, aby se vyhnuli problémům souvisejícím se zabezpečením. Například během instalace by měla být do seznamu řízení přístupu (ACL) přidána dll profileru, aby ji uživatel se zlými úmysly nemohl změnit.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Kombinace spravovaného a nespravovaného kódu v profileru kódu

Nesprávně napsaný profiler může způsobit cyklické odkazy na sebe sama, výsledkem nepředvídatelné chování.

Kontrola rozhraní CLR profilování rozhraní API může vytvořit dojem, že můžete napsat profiler, který obsahuje spravované a nespravované součásti, které volají navzájem prostřednictvím interop modelu COM nebo nepřímých volání.

I když je to možné z hlediska návrhu, profilování rozhraní API nepodporuje spravované součásti. Profiler CLR musí být zcela nespravované. Pokusy o kombinaci spravovaného a nespravovaného kódu v profileru CLR mohou způsobit narušení přístupu, selhání programu nebo zablokování. Spravované součásti profileru budou vypalovat události zpět do jejich nespravovaných součástí, které by následně znovu volaly spravované součásti, což by vedlo k cyklické odkazy.

Jediné umístění, kde může profiler CLR bezpečně volat spravovaný kód, je v těle metody zprostředkujícíjazyk společnosti Microsoft (MSIL). Doporučeným postupem pro úpravu těla MSIL je použití metod rekompilace JIT v rozhraní [ICorProfilerCallback4.](icorprofilercallback4-interface.md)

Je také možné použít starší metody instrumentace k úpravě MSIL. Před dokončením kompilace funkce just-in-time (JIT) může profiler vložit spravovaná volání v těle MSIL metody a pak jit-kompilaci (viz [Metoda ICorProfilerInfo::GetILFunctionBody).](icorprofilerinfo-getilfunctionbody-method.md) Tuto techniku lze úspěšně použít pro selektivní instrumentaci spravovaného kódu nebo ke shromažďování statistik a údajů o výkonu o JIT.

Případně profiler kódu můžete vložit nativní háčky v těle MSIL každé spravované funkce, která volá do nespravovaného kódu. Tato technika může být použita pro instrumentaci a pokrytí. Například profiler kódu může vložit háčky instrumentace za každý blok MSIL, aby bylo zajištěno, že blok byl proveden. Modifikace těla MSIL metody je velmi delikátní operace a existuje mnoho faktorů, které je třeba vzít v úvahu.

## <a name="profiling-unmanaged-code"></a>Profilování nespravovaného kódu

Rozhraní API profilování běžného jazyka (CLR) poskytuje minimální podporu pro profilování nespravovaného kódu. K dispozici je následující funkce:

- Výčet řetězce zásobníku. Tato funkce umožňuje profileru kódu určit hranici mezi spravovaným kódem a nespravovaným kódem.

- Určení, zda řetězec zásobníku odpovídá spravovanému kódu nebo nativnímu kódu.

Ve verzích .NET Framework 1.0 a 1.1 jsou tyto metody k dispozici prostřednictvím podmnožiny rozhraní CLR pro ladění. Jsou definovány v souboru CorDebug.idl.

V rozhraní .NET Framework 2.0 a novějším můžete pro tuto funkci použít metodu [ICorProfilerInfo2::DoStackSnapshot.](icorprofilerinfo2-dostacksnapshot-method.md)

## <a name="using-com"></a>Použití com

Přestože profilování rozhraní jsou definovány jako rozhraní COM, modul CLR (COMMON Language) není ve skutečnosti inicializovat COM používat tato rozhraní. Důvodem je, aby se zabránilo nutnosti nastavit model zřetězení pomocí funkce [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) dříve, než spravovanou aplikaci měl možnost zadat požadovaný model zřetězení. Podobně profiler sám by neměl `CoInitialize`volat , protože může vybrat model podprocesu, který je nekompatibilní s aplikací, která je profilována a může způsobit selhání aplikace.

## <a name="call-stacks"></a>Zásobníky volání

Profilování rozhraní API poskytuje dva způsoby, jak získat zásobníky volání: metoda snímek zásobníku, která umožňuje řídké shromažďování zásobníků volání a stín zásobníku metoda, která sleduje zásobník volání v každém okamžiku.

### <a name="stack-snapshot"></a>Snímek zásobníku

Snímek zásobníku je trasování zásobníku vlákna v okamžiku v čase. Profilování rozhraní API podporuje trasování spravovaných funkcí v zásobníku, ale ponechá trasování nespravovaných funkcí profiler vlastní zásobníku walker.

Další informace o tom, jak naprogramovat profiler pro chod spravované hromádky, naleznete v metodě [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) v této sadě dokumentace a [v rozhraní .NET Framework 2.0: Basics and Beyond](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).

### <a name="shadow-stack"></a>Stínový zásobník

Použití metody snímek příliš často můžete rychle vytvořit problém s výkonem. Pokud chcete trvat trasování zásobníku často, váš profiler by místo toho vytvořit zásobník stín pomocí [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), [FunctionTailcall2](functiontailcall2-function.md)a [ICorProfilerCallback2](icorprofilercallback2-interface.md) volání výjimek. Zásobník stínů je vždy aktuální a lze jej rychle zkopírovat do úložiště vždy, když je potřeba snímek zásobníku.

Stín zásobníku může získat argumenty funkce, vrácené hodnoty a informace o obecné instance. Tyto informace jsou k dispozici pouze prostřednictvím stínového zásobníku a lze je získat při předání ovládacího prvku funkci. Tyto informace však nemusí být k dispozici později během spuštění funkce.

## <a name="callbacks-and-stack-depth"></a>Zpětná volání a hloubka zásobníku

Zpětná volání profileru mohou být vydána za velmi omezených podmínek zásobníku a přetečení zásobníku v zpětném volání profileru povede k okamžitému ukončení procesu. Profiler by měl ujistěte se, že použití co nejmenší zásobníku v reakci na zpětná volání. Pokud profiler je určen pro použití proti procesy, které jsou robustní proti přetečení zásobníku, profiler sám by také neměl a tím zabránit aktivaci přetečení zásobníku.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Nastavení prostředí profilace](setting-up-a-profiling-environment.md)|Vysvětluje, jak inicializovat profiler, nastavit oznámení událostí a profilovat službu systému Windows.|
|[Rozhraní pro profilaci](profiling-interfaces.md)|Popisuje nespravovaná rozhraní, která používá profilovací rozhraní API.|
|[Profilace globálních statických funkcí](profiling-global-static-functions.md)|Popisuje nespravované globální statické funkce, které používá profilovací rozhraní API.|
|[Výčty pro profilaci](profiling-enumerations.md)|Popisuje nespravované výčty, které používá profilovací rozhraní API.|
|[Struktury pro profilaci](profiling-structures.md)|Popisuje nespravované struktury, které používá profilovací rozhraní API.|
