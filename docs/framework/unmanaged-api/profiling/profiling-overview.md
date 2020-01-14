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
ms.openlocfilehash: a13470b970b35a2f6f088fd305ba455167c8e107
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937820"
---
# <a name="profiling-overview"></a>Přehled profilace

Profiler je nástroj, který monitoruje provádění jiné aplikace. Profiler modulu CLR (Common Language Runtime) je dynamická knihovna (DLL), která se skládá z funkcí, které přijímají zprávy a odesílají zprávy do modulu CLR pomocí Profilování rozhraní API. Knihovna DLL profileru je načtena modulem CLR v době běhu.

Tradiční nástroje pro profilaci se zaměřují na měření spuštění aplikace. To znamená, že měří čas strávený v každé funkci nebo využití paměti aplikace v čase. Rozhraní API profilování cílí na širší třídu diagnostických nástrojů, jako jsou například nástroje pro pokrytí kódu a dokonce i rozšířené pomůcky pro ladění. Tato použití jsou všechna Diagnostika v podstatě. Rozhraní API profilování nejen měří, ale také sleduje spuštění aplikace. Z tohoto důvodu by rozhraní API profilování nemělo být nikdy používáno aplikací samotné a spuštění aplikace by nemělo záviset na (nebo být ovlivněno) profilerem.

Profilace aplikace CLR vyžaduje větší podporu než sestavení zkompilovaného strojového kódu v konvenci profilace. Důvodem je, že CLR zavádí koncepty, jako například domény aplikace, uvolňování paměti, spravované zpracování výjimek, kompilaci JIT (just-in-time) kódu (převod Microsoft Intermediate Language nebo MSIL, Code do nativního strojového kódu) a podobné funkce. Konvenční mechanismy profilace nemůžou identifikovat nebo poskytnout užitečné informace o těchto funkcích. Rozhraní API profilování poskytuje tyto chybějící informace efektivně s minimálním dopadem na výkon CLR a profilované aplikace.

Kompilace JIT za běhu nabízí dobré příležitosti pro profilování. Rozhraní API profilování umožňuje profileru změnit datový proud kódu MSIL v paměti pro rutinu předtím, než je kompilace JIT zkompilována. Tímto způsobem může Profiler dynamicky přidat kód instrumentace k určitým rutinám, které potřebují hlubší šetření. I když je tento přístup možný v konvenčních scénářích, je mnohem snazší implementovat CLR pomocí Profilování rozhraní API.

## <a name="the-profiling-api"></a>Rozhraní API profilování

Rozhraní API profilování se obvykle používá k zápisu *profileru kódu*, což je program, který sleduje spuštění spravované aplikace.

Rozhraní API profileru používá profil DLL profileru, který se načte do stejného procesu jako aplikace, která se profiluje. Knihovna DLL profileru implementuje rozhraní zpětného volání ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) v .NET Framework verze 1,0 a 1,1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) ve verzi 2,0 a novější). CLR volá metody v tomto rozhraní, aby upozornil Profiler událostí v profilované procesu. Profiler může volat zpět do modulu runtime pomocí metod v rozhraních [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) a [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) k získání informací o stavu profilované aplikace.

> [!NOTE]
> Pouze část shromažďování dat v rámci řešení profileru by měla být spuštěna ve stejném procesu jako profilovaná aplikace. Veškeré uživatelské rozhraní a analýzu dat by se měly provádět v samostatném procesu.

Následující obrázek ukazuje, jak knihovna DLL profileru komunikuje s aplikací, která je profilovaná a CLR.

![Snímek obrazovky, který zobrazuje architekturu profilace.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Rozhraní pro oznamování

[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) lze považovat za rozhraní oznámení. Tato rozhraní se skládají z metod, jako jsou [ClassLoadStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)a [JITCompilationStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Pokaždé, když CLR načte nebo uvolní třídu, zkompiluje funkci a tak dále, volá odpovídající metodu v rozhraní `ICorProfilerCallback` nebo `ICorProfilerCallback2` profileru.

Profiler může například měřit výkon kódu prostřednictvím dvou funkcí oznámení: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) a [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Slouží pouze k časovému razítku každého oznámení, nashromáždí výsledky a vytvoří výstup seznamu, který označuje, které funkce při provádění aplikace spotřebují nejvíce času procesoru nebo hodin na zdi.

### <a name="the-information-retrieval-interfaces"></a>Rozhraní pro načítání informací

Další hlavní rozhraní zapojená do profilace jsou [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) a [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profiler volá tato rozhraní podle potřeby, aby získal další informace, které vám pomůžou s analýzou. Například vždy, když CLR volá funkci [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) , poskytuje identifikátor funkce. Profiler může získat další informace o této funkci voláním metody [ICorProfilerInfo2:: GetFunctionInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) pro zjištění nadřazené třídy funkce, jejího názvu a tak dále.

## <a name="supported-features"></a>Podporované funkce

Rozhraní API profilování poskytuje informace o nejrůznějších událostech a akcích, ke kterým dochází v modulu CLR (Common Language Runtime). Tyto informace můžete použít k monitorování vnitřních pracovních postupů procesů a k analýze výkonu aplikace .NET Framework.

Rozhraní API profilování načte informace o následujících akcích a událostech, ke kterým dochází v modulu CLR:

- Události spuštění a vypnutí CLR

- Události vytvoření a vypnutí domény aplikace.

- Události načítání a uvolňování sestavení

- Události načítání a uvolňování modulu

- Vytváření a zničení událostí modelu COM vtable.

- Kompilace just-in-time (JIT) a události pro rozteč kódu.

- Události načítání a uvolňování třídy.

- Události vytvoření a zničení vlákna.

- Události vstupu a výstupu funkce

- Výjimky.

- Přechody mezi spravovaným a nespravovaným kódem.

- Přechody mezi různými kontexty modulu runtime.

- Informace o pozastaveních modulu runtime.

- Informace o haldě běhové paměti a aktivitě uvolňování paměti.

Rozhraní API profilování se dá volat z libovolného (nespravovaného) jazyka kompatibilního s modelem COM.

Rozhraní API je efektivní z hlediska využití procesoru a paměti. Profilace nezahrnuje změny profilované aplikace, které jsou dostatečně významné, aby způsobily zavádějící výsledky.

Rozhraní API profilování je užitečné pro vzorkování i pro nástroje, které nejsou vzorkovací. *Profiler vzorkování* kontroluje profil v pravidelných taktech, například 5 milisekund od sebe. *Profiler bez vzorkování* je informován o události synchronně s vláknem, které způsobuje událost.

### <a name="unsupported-functionality"></a>Nepodporované funkce

Rozhraní API profilování nepodporuje následující funkce:

- Nespravovaný kód, který musí být profilovaná pomocí konvenčních metod Win32. Profiler CLR ale obsahuje přechodné události pro určení hranic mezi spravovaným a nespravovaným kódem.

- Vlastní úprava aplikací, které upravují jejich vlastní kód pro účely, jako je například programování orientované na jednotlivé aspekty.

- Kontrola hranic, protože rozhraní API profilování tyto informace neposkytuje. CLR poskytuje vnitřní podporu pro kontrolu hranic veškerého spravovaného kódu.

- Vzdálené profilování, které se nepodporuje z následujících důvodů:

  - Vzdálené profilování rozšiřuje dobu provádění. Pokud používáte rozhraní profilování, je nutné minimalizovat dobu spuštění, aby se výsledky profilace neprojevily. To platí zejména při monitorování výkonu provádění. Vzdálené profilování však není omezením, když jsou rozhraní profilování používána k monitorování využití paměti nebo k získání běhových informací o rámcích zásobníku, objektech a tak dále.

  - Profiler kódu CLR musí zaregistrovat jedno nebo více rozhraní zpětného volání s modulem runtime v místním počítači, na kterém je spuštěn profilovaná aplikace. Tím se omezí možnost vytvářet Profiler vzdáleného kódu.

- Profilace v produkčním prostředí s požadavky na vysokou dostupnost. Rozhraní API profilování bylo vytvořeno za účelem podpory diagnostiky při vývoji. Neprošlo přísným testováním vyžadovaným pro podporu produkčních prostředí.

## <a name="notification-threads"></a>Vlákna oznámení

Ve většině případů vlákno, které generuje událost, také spouští oznámení. Taková oznámení (například [FunctionEnter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) a [FunctionLeave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) nemusejí zadávat explicitní `ThreadID`. Profiler se také může rozhodnout použít místní úložiště vlákna k ukládání a aktualizaci bloků analýz namísto indexování bloků analýzy v globálním úložišti, a to na základě `ThreadID` ovlivněného vlákna.

Všimněte si, že tato zpětná volání nejsou serializována. Uživatelé musí chránit svůj kód vytvořením datových struktur bezpečných pro přístup z více vláken a uzamknutím kódu profileru, pokud je to nutné, aby se zabránilo paralelnímu přístupu z více vláken Proto v některých případech můžete obdržet neobvyklou posloupnost zpětných volání. Předpokládejme například, že spravovaná aplikace vytváří dvě vlákna, která spouštějí stejný kód. V tomto případě je možné přijmout událost [ICorProfilerCallback:: JITCompilationStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) pro určitou funkci z jednoho vlákna a zpětného volání `FunctionEnter` z druhého vlákna před příjmem zpětného volání [ICorProfilerCallback:: JITCompilationFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) . V takovém případě bude uživatel obdržet `FunctionEnter` zpětného volání pro funkci, která pravděpodobně nebyla dosud plně zkompilována za běhu (just-in-time).

## <a name="security"></a>Zabezpečení –

Knihovna DLL profileru je nespravovaná knihovna DLL, která se spouští jako součást modulu pro spuštění společného jazykového modulu runtime. V důsledku toho kód v profileru DLL nepodléhá omezením zabezpečení přístupu spravovaného kódu. Jediným omezením v knihovně DLL profileru jsou ta, která je uložená operačním systémem pro uživatele, který používá profilované aplikace.

Autoři profileru by měli přijmout vhodná opatření, aby se předešlo problémům souvisejícím se zabezpečením. Během instalace by se například měl profil DLL profileru přidat do seznamu řízení přístupu (ACL), aby ho uživatel se zlými úmysly nemohl změnit.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Kombinování spravovaného a nespravovaného kódu v profileru kódu

Nesprávně napsaný profiler může způsobit cyklické odkazy na sebe sama, což vede k nepředvídatelnému chování.

Kontrola rozhraní API profilování CLR může vytvořit dojem, že můžete napsat Profiler, který obsahuje spravované a nespravované součásti, které jsou vzájemně volány prostřednictvím zprostředkovatele komunikace s objekty COM nebo nepřímými voláními.

I když je to možné z perspektivy návrhu, rozhraní API profilování nepodporuje spravované součásti. Profiler CLR musí být zcela nespravovaný. Pokusy o kombinování spravovaného a nespravovaného kódu v profileru CLR můžou způsobit narušení přístupu, selhání programu nebo zablokování. Spravované součásti profileru spustí události zpět do jejich nespravovaných komponent, které by následně znovu volaly spravované komponenty, což vede k cyklickým odkazům.

Jediné místo, kde Profiler CLR může bezpečně volat spravovaný kód, je v těle metody jazyka MSIL (Microsoft Intermediate Language). Doporučený postup pro úpravu těla jazyka MSIL je použití metod rekompilace JIT v rozhraní [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) .

Je také možné použít starší metody instrumentace pro úpravu jazyka MSIL. Před dokončením kompilace funkce just-in-time (JIT) může Profiler vložit spravovaná volání do těla jazyka MSIL metody a následně je zkompilovat JIT (viz metoda [ICorProfilerInfo:: GetILFunctionBody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) ). Tato technika se dá úspěšně použít pro selektivní instrumentaci spravovaného kódu nebo pro shromažďování dat o statistice a výkonu o JIT.

Případně může Profiler kódu vložit nativní háky v těle jazyka MSIL každé spravované funkce, která volá do nespravovaného kódu. Tato technika se dá použít k instrumentaci a pokrytí. Například Profiler kódu může vložit háky instrumentace po každém bloku MSIL, aby bylo zajištěno, že byl blok proveden. Modifikace těla jazyka MSIL metody je velmi jemná operace a existuje mnoho faktorů, které je třeba vzít v úvahu.

## <a name="profiling-unmanaged-code"></a>Profilování nespravovaného kódu

Rozhraní API pro profilaci modulu CLR (Common Language Runtime) poskytuje minimální podporu pro profilování nespravovaného kódu. K dispozici jsou následující funkce:

- Výčet řetězů zásobníku. Tato funkce umožňuje profileru kódu určit hranici mezi spravovaným kódem a nespravovaným kódem.

- Určení, zda řetěz zásobníku odpovídá spravovanému kódu nebo nativnímu kódu.

V .NET Framework verzích 1,0 a 1,1 jsou tyto metody k dispozici prostřednictvím dílčí sady v rámci procesu rozhraní API pro ladění CLR. Jsou definovány v souboru CorDebug. idl.

V .NET Framework 2,0 a novějších můžete pro tuto funkci použít metodu [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .

## <a name="using-com"></a>Používání modelu COM

I když jsou rozhraní profilace definována jako rozhraní COM, modul CLR (Common Language Runtime) ve skutečnosti neinicializuje model COM pro použití těchto rozhraní. Důvodem je, že nemusíte nastavovat model vláken pomocí funkce [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) předtím, než spravovaná aplikace měla možnost určit požadovaný model vláken. Podobně samotný Profiler by neměl volat `CoInitialize`, protože může vybrat model vláken, který je nekompatibilní s aplikací, která je profilovaná a může způsobit selhání aplikace.

## <a name="call-stacks"></a>Zásobníky volání

Rozhraní API profilování poskytuje dva způsoby, jak získat zásobníky volání: metodu snímku zásobníku, která umožňuje zhuštěné shromažďování zásobníků volání, a metodu stínového zásobníku, která sleduje zásobník volání při každém okamžitém běhu.

### <a name="stack-snapshot"></a>Snímek zásobníku

Snímek zásobníku je trasování zásobníku vlákna v okamžitém čase. Rozhraní API profilování podporuje trasování spravovaných funkcí v zásobníku, ale opustí trasování nespravovaných funkcí do vlastního zásobníku prohlížeč profileru.

Další informace o tom, jak profiler naprogramovat, aby provedl spravované zásobníky, najdete v části [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) v této dokumentaci a [v zásobníku profileru v .NET Framework 2,0: základy a mimo ni](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).

### <a name="shadow-stack"></a>Stínový zásobník

Použití metody Snapshot moc často může rychle vytvořit problém s výkonem. Pokud chcete přebírat trasování zásobníku často, váš Profiler by měl vytvořit stínový zásobník pomocí zpětného volání výjimek [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) . Stínový zásobník je vždycky aktuální a dá se rychle zkopírovat do úložiště, kdykoli je potřeba snímek zásobníku.

Stínový zásobník může získat argumenty funkce, vracet hodnoty a informace o obecných instancích. Tyto informace jsou k dispozici pouze prostřednictvím stínového zásobníku a lze je získat, pokud je ovládací prvek předán funkci. Tyto informace ale nemusí být k dispozici později během spuštění funkce.

## <a name="callbacks-and-stack-depth"></a>Zpětná volání a Hloubka zásobníku

Zpětná volání profileru mohou být vydávána v podmínkách s velmi omezenými zásobníky a přetečení zásobníku v rámci zpětného volání profileru vede k okamžitému ukončení procesu. Profiler by měl v reakci na zpětná volání používat co nejmenší zásobník. Pokud je profiler určený pro použití proti procesům, které jsou robustní proti přetečení zásobníku, měl by samotný Profiler také zabránit spuštění přetečení zásobníku.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Nastavení prostředí profilace](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Vysvětluje, jak inicializovat Profiler, nastavit oznámení událostí a profilovat službu systému Windows.|
|[Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Popisuje nespravovaná rozhraní, která používá profilování API.|
|[Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Popisuje nespravované globální statické funkce, které používá profilování API.|
|[Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Popisuje nespravované výčty, které používá profilování API.|
|[Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Popisuje nespravované struktury, které používá profilování API.|
