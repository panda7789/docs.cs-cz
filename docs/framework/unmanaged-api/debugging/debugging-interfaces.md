---
title: Debugging – rozhraní
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179167"
---
# <a name="debugging-interfaces"></a>Debugging – rozhraní
Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozhraní ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-interface.md)\
 Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.  
  
 [Rozhraní ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)\
 Poskytuje metodu zpětného volání pro `EnumMemoryRegions` hlášení ladicího programu, což je výsledek pokusu o výčet zadané oblasti paměti.  
  
 [Rozhraní ICLRDataTarget](iclrdatatarget-interface.md)\
 Poskytuje metody pro interakci s cílovým procesem CLR.  
  
 [Rozhraní ICLRDataTarget2](iclrdatatarget2-interface.md)\
 `ICLRDataTarget` Podtřída, která se používá vrstvou služeb přístupu k datům k manipulaci s oblastmi virtuální paměti v cílovém procesu.  
  
 [Rozhraní ICLRDataTarget3](iclrdatatarget3-interface.md)\
 Podtřída [ICLRDataTarget2,](iclrdatatarget2-interface.md) která poskytuje přístup k informacím o výjimce.  
  
 [Rozhraní ICLR Debugging](iclrdebugging-interface.md)\
 Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
 [Rozhraní ICLR DebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)\
 Zahrnuje [metodu ProvideLibrary Method,](iclrdebugginglibraryprovider-providelibrary-method.md) která získá rozhraní pro zpětné volání zprostředkovatele knihovny, které umožňuje knihovny ladění specifické pro běžné moduly runtime specifické pro zpracování a načtení na vyžádání.  
  
 [Rozhraní ICLRMetadataLocator](iclrmetadatalocator-interface.md)\
 Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.  
  
 [Rozhraní ICorDebug](icordebug-interface.md)\
 Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.  
  
 [Rozhraní ICorDebugAppDomain](icordebugappdomain-interface.md)\
 Poskytuje metody pro ladění domén aplikace.  
  
 [Rozhraní ICorDebugAppDomain2](icordebugappdomain2-interface.md)\
 Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef. Toto rozhraní je `ICorDebugAppDomain` rozšíření rozhraní.  
  
 [Rozhraní ICorDebugAppDomain3](icordebugappdomain3-interface.md)\
 Poskytuje metody pro práci s typy prostředí Windows Runtime v doméně aplikace. Toto rozhraní je `ICorDebugAppDomain` rozšíření `ICorDebugAppDomain2` a rozhraní.  
  
 [Rozhraní ICorDebugAppDomain4](icordebugappdomain4-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugAppDomain](icordebugappdomain-interface.md) získat spravovaný objekt z com volatelné obálky.  
  
 [Rozhraní ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)\
 Poskytuje metodu, která vrací `ICorDebugAppDomain` zadaný počet hodnot začínajících na dalším místě ve výčtu.  
  
 [Rozhraní ICorDebugArrayValue](icordebugarrayvalue-interface.md)\
 `ICorDebugHeapValue` Podtřída, která představuje jednorozměrné nebo vícerozměrné pole.  
  
 [Rozhraní ICorDebugAssembly](icordebugassembly-interface.md)\
 Představuje sestavení.  
  
 [Rozhraní ICorDebugAssembly2](icordebugassembly2-interface.md)\
 Představuje sestavení. Toto rozhraní je `ICorDebugAssembly` rozšíření rozhraní.  
  
 [Rozhraní ICorDebugAssembly3](icordebugassembly3-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugAssembly](icordebugassembly-interface.md) poskytnout podporu pro sestavení kontejnerů a jejich obsažené sestavení. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugAssembly` pole.  
  
 [Rozhraní ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)\
 Poskytuje čítač pro seznam [cordebugBlockingObject](cordebugblockingobject-structure.md) struktury.  
  
 [Rozhraní ICorDebugBoxValue](icordebugboxvalue-interface.md)\
 `ICorDebugHeapValue` Podtřída, která představuje objekt třídy s krabicovou hodnotou.  
  
 [Rozhraní ICorDebugBreakpoint](icordebugbreakpoint-interface.md)\
 Představuje zarážku ve funkci nebo bod sledování na hodnotě.  
  
 [Rozhraní ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugBreakpoint` pole.  
  
 [Rozhraní ICorDebugChain](icordebugchain-interface.md)\
 Představuje segment fyzického nebo logického zásobníku volání.  
  
 [Rozhraní ICorDebugChainEnum](icordebugchainenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugChain` pole.  
  
 [Rozhraní ICorDebugClass](icordebugclass-interface.md)\
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ `ICorDebugClass` obecný, představuje neinstance obecný typ.  
  
 [Rozhraní ICorDebugClass2](icordebugclass2-interface.md)\
 Představuje obecnou třídu nebo třídu s <xref:System.Type>parametrem metody typu . Toto rozhraní `ICorDebugClass`rozšiřuje .  
  
 [Rozhraní ICorDebugCode](icordebugcode-interface1.md)\
 Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
 [Rozhraní ICorDebugCode2](icordebugcode2-interface.md)\
 Poskytuje metody, které `ICorDebugCode`rozšiřují možnosti .  
  
 [Rozhraní ICorDebugCode3](icordebugcode3-interface.md)\
 Poskytuje metodu, která rozšiřuje [ICorDebugCode](icordebugcode-interface1.md) a [ICorDebugCode2](icordebugcode2-interface.md) poskytnout informace o spravované vrácená hodnota.  
  
 [Rozhraní ICorDebugCode4](icordebugcode4-interface.md)\
 Poskytuje metodu, která umožňuje ladicí program pro výčet místníproměnné a argumenty ve funkci.  
  
 [Rozhraní ICorDebugCodeEnum](icordebugcodeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugCode` pole.  
  
 [Rozhraní ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)\
 Poskytuje metody pro načtení objektů z mezipaměti rozhraní.  
  
 [Rozhraní ICorDebugContext](icordebugcontext-interface.md)\
 Představuje objekt kontextu. Toto rozhraní zatím nebylo implementováno.  
  
 [Rozhraní ICorDebugController](icordebugcontroller-interface.md)\
 Představuje obor, <xref:System.Diagnostics.Process> nebo nebo <xref:System.AppDomain>, ve kterém může být řízen kontext spuštění kódu.  
  
 [Rozhraní ICorDebugDataTarget](icordebugdatatarget-interface.md)\
 Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
 [Rozhraní ICorDebugDataTarget2](icordebugdatatarget2-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugDataTarget.](icordebugdatatarget-interface.md) **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugDataTarget3](icordebugdatatarget3-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) poskytnout informace o načtených modulů. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugDebugEvent](icordebugdebugevent-interface.md)\
 Definuje základní rozhraní, ze `ICorDebug` kterého jsou odvozeny všechny události ladění. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)\
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [Rozhraní ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)\
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [Rozhraní ICorDebugEnum](icordebugenum-interface1.md)\
 Slouží jako abstraktní základní rozhraní pro enumerátory ladění.  
  
 [Rozhraní ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)\
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [Rozhraní ICorDebugEval](icordebugeval-interface.md)\
 Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
 [Rozhraní ICorDebugEval2](icordebugeval2-interface.md)\
 Rozšiřuje `ICorDebugEval` poskytovat podporu pro obecné typy.  
  
 [Rozhraní ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)\
 Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí výjimky. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)\
 Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.  
  
 [Rozhraní ICorDebugExceptionObject](icordebugexceptionobjectvalue-interface.md)\
 Rozšiřuje rozhraní [ICorDebugObjectValue](icordebugobjectvalue-interface.md) poskytnout informace o trasování zásobníku ze spravovaného objektu výjimky.  
  
 [Rozhraní ICorDebugFrame](icordebugframe-interface.md)\
 Představuje snímek aktuálního zásobníku.  
  
 [Rozhraní ICorDebugFrameEnum](icordebugframeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugFrame` pole.  
  
 [Rozhraní ICorDebugFunction](icordebugfunction-interface1.md)\
 Představuje spravovanou funkci nebo metodu.  
  
 [Rozhraní ICorDebugFunction2](icordebugfunction2-interface.md)\
 Logicky rozšiřuje `ICorDebugFunction` poskytovat podporu pro pouze můj kód krok-through ladění.  
  
 [Rozhraní ICorDebugFunction3](icordebugfunction3-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugFunction](icordebugfunction-interface1.md) poskytnout přístup ke kódu z požadavku ReJIT.  
  
 [Rozhraní ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkce.  
  
 [Rozhraní ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)\
 Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
 [Rozhraní ICorDebugGenericValue](icordebuggenericvalue-interface.md)\
 `ICorDebugValue` Podtřída, která platí pro všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
 [Rozhraní ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)\
 Poskytuje čítač výčtu pro objekt, který `ICorDebugType` mapuje identifikátory GUID a jejich odpovídající objekty.  
  
 [Rozhraní ICorDebugHandleValue](icordebughandlevalue-interface.md)\
 `ICorDebugReferenceValue` Podtřída, která představuje referenční hodnotu, na kterou ladicí program vytvořil popisovač pro uvolňování paměti.  
  
 [Rozhraní ICorDebugHeapEnum](icordebugheapenum-interface.md)\
 Poskytuje enumerátor pro objekty na spravované haldě.  
  
 [Rozhraní ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)\
 Poskytuje enumerátor pro oblasti paměti spravované haldy.  
  
 [Rozhraní ICorDebugHeapValue](icordebugheapvalue-interface.md)\
 `ICorDebugValue` Podtřída, která představuje objekt, který byl shromážděn uvolňováníclr.  
  
 [Rozhraní ICorDebugHeap2](icordebugheapvalue2-interface1.md)\
 `ICorDebugHeapValue` Rozšíření, které poskytuje podporu pro runtime popisovače.  
  
 [Rozhraní ICorDebugHeapValue3](icordebugheapvalue3-interface.md)\
 Zpřístupní vlastnosti uzamčení sledování objektů.  
  
 [Rozhraní ICorDebugILCode](icordebugilcode-interface.md)\
 Představuje segment kódu zprostředkujícího jazyka (IL).  
  
 [Rozhraní ICorDebugILCode2](icordebugilcode2-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugILCode](icordebugilcode-interface.md) poskytnout metody, které vrátí token pro podpis místní proměnné funkce a které mapují profiler instrumentované zprostředkující jazyk (IL) posuny původní metody IL posuny.  
  
 [Rozhraní ICorDebugILFrame](icordebugilframe-interface.md)\
 Představuje rámec zásobníku kódu MSIL.  
  
 [Rozhraní ICorDebugILFrame2](icordebugilframe2-interface.md)\
 Logické rozšíření `ICorDebugILFrame`.  
  
 [Rozhraní ICorDebugILFrame3](icordebugilframe3-interface.md)\
 Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.  
  
 [Rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)\
 Poskytuje metody, které umožňují přístup k místním proměnným a kódu v rámci zásobníku kódu zprostředkujícího jazyka (IL). Parametr určuje, zda ladicí program má přístup k proměnným a kód přidán v profileru ReJIT instrumentace.  
  
 [Rozhraní ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)\
 Představuje informace o symbolu ladění pro pole instance. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugInternalFrame](icordebuginternalframe-interface.md)\
 Určuje typy rámců pro ladicí program.  
  
 [Rozhraní ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)\
 Obsahuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k objektům [ICorDebugFrame.](icordebugframe-interface.md)  
  
 [Rozhraní ICorDebugLoadedModule](icordebugloadedmodule-interface.md)\
 Obsahuje informace o načteném modulu. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)\
 Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
 [Rozhraní ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)\
 Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA). `ICorDebugManagedCallback2`je logickým `ICorDebugManagedCallback`rozšířením .  
  
 [Rozhraní ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)\
 Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.  
  
 [Rozhraní ICorDebugMDA](icordebugmda-interface.md)\
 Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
 [Rozhraní ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)\
 Představuje vyrovnávací paměť v paměti. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)\
 Obsahuje informace o sloučeném sestavení. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)\
 Poskytuje informace metadat k ladicímu programu.  
  
 [Rozhraní ICorDebugModule](icordebugmodule-interface.md)\
 Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).  
  
 [Rozhraní ICorDebugModule2](icordebugmodule2-interface.md)\
 Slouží jako logické `ICorDebugModule`rozšíření .  
  
 [Rozhraní ICorDebugModule3](icordebugmodule3-interface.md)\
 Vytvoří čtečku symbolů pro dynamický modul.  
  
 [Rozhraní ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` poskytovat přístup ke konkrétním modulům.  
  
 [Rozhraní ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)\
 Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugModuleEnum](icordebugmoduleenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugModule` pole.  
  
 [Rozhraní ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)\
 Rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.  
  
 [Rozhraní ICorDebugNativeFrame](icordebugnativeframe-interface.md)\
 Specializovaná implementace `ICorDebugFrame` pro nativní rámce.  
  
 [Rozhraní ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)\
 Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.  
  
 [Rozhraní ICorDebugObjectEnum](icordebugobjectenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává pole objektů podle jejich relativní virtuální adresy (RVAs).  
  
 [Rozhraní ICorDebugObjectValue](icordebugobjectvalue-interface.md)\
 `ICorDebugValue` Podtřída, která představuje hodnotu, která obsahuje objekt.  
  
 [Rozhraní ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)\
 Rozšiřuje `ICorDebugObjectValue` se na podporu dědičnosti a přepsání.  
  
 [Rozhraní ICorDebugProcess](icordebugprocess-interface.md)\
 Představuje proces, který spouští spravovaný kód.  
  
 [Rozhraní ICorDebugProcess2](icordebugprocess2-interface1.md)\
 Logické rozšíření `ICorDebugProcess`.  
  
 [Rozhraní ICorDebugProcess3](icordebugprocess3-interface.md)\
 Řídí vlastní oznámení ladicího programu.

 [Rozhraní ICorDebugProcess4](icordebugprocess4-interface.md)\
 Poskytuje podporu pro řízení provádění mimo proces.
  
 [Rozhraní ICorDebugProcess5](icordebugprocess5-interface.md)\
 Rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) pro podporu přístupu ke spravované haldě, poskytuje informace o uvolňování paměti spravovaných objektů a k určení, zda ladicí program načte obrazy z místní mezipaměti nativního obrázku aplikace.  
  
 [Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) povolit funkce, jako je dekódování spravované ladicí události, které jsou kódovány v nativní výjimky ladění událostí a rozdělení virtuálního modulu. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugProcess7](icordebugprocess7-interface.md)\
 Poskytuje metodu, která konfiguruje ladicí program pro zpracování aktualizací metadat v paměti v cílovém procesu.  
  
 [Rozhraní ICorDebugProcess8](icordebugprocess8-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) pro povolení nebo zakázání určitých typů zpětná volání výjimek [ICorDebugManagedCallback2.](icordebugmanagedcallback2-interface.md)  
  
 [Rozhraní ICorDebugProcessEnum](icordebugprocessenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugProcess` pole.  
  
 [Rozhraní ICorDebugReferenceValue](icordebugreferencevalue-interface.md)\
 `ICorDebugValue` Podtřída, která podporuje typy odkazů.  
  
 [Rozhraní ICorDebugRegisterSet](icordebugregisterset-interface.md)\
 Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
 [Rozhraní ICorDebugRegisterSet2](icordebugregisterset2-interface.md)\
 Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.  
  
 [Vzdálené rozhraní ICorDebug](icordebugremote-interface.md)\
 Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.  
  
 [Rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md)\
 Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.  
  
 [Rozhraní ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)\
 Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
 [Rozhraní ICorDebugStackWalk](icordebugstackwalk-interface.md)\
 Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
 [Rozhraní ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)\
 Představuje informace o symbolu ladění pro statické pole. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugStepper](icordebugstepper-interface.md)\
 Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
 [Rozhraní ICorDebugStepper2](icordebugstepper2-interface1.md)\
 Poskytuje podporu ladění Pouze můj kód (JMC).  
  
 [Rozhraní ICorDebugStepperEnum](icordebugstepperenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugStepper` pole.  
  
 [Rozhraní ICorDebugStringValue](icordebugstringvalue-interface.md)\
 `ICorDebugHeapValue` Podtřída, která platí pro řetězcové hodnoty.  
  
 [Rozhraní ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)\
 Poskytuje metody, které lze použít k načtení informací o symbolu ladění. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)\
 Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) načíst další informace o symbolu ladění. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugThread](icordebugthread-interface.md)\
 Představuje vlákno v procesu. Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
 [Rozhraní ICorDebugThread2](icordebugthread2-interface.md)\
 Slouží jako logické `ICorDebugThread`rozšíření .  
  
 [Rozhraní ICorDebugThread3](icordebugthread3-interface.md)\
 Poskytuje vstupní bod [iCorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.  
  
 [Rozhraní ICorDebugThread4](icordebugthread4-interface.md)\
 Poskytuje informace o blokování vlákna.  
  
 [Rozhraní ICorDebugThreadEnum](icordebugthreadenum-interface1.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugThread` pole.  
  
 [Rozhraní ICorDebugType](icordebugtype-interface.md)\
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ `ICorDebugType` obecný, představuje instance obecný typ.  
  
 [Rozhraní ICorDebugType2](icordebugtype2-interface.md)\
 Rozšiřuje rozhraní [ICorDebugType](icordebugtype-interface.md) načíst identifikátor typu základního typu nebo komplexní (uživatelem definované) typu.  
  
 [Rozhraní ICorDebugTypeEnum](icordebugtypeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugType` pole.  
  
 [Rozhraní ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)\
 Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.  
  
 [Hodnota ICorDebugValue](icordebugvalue-interface.md)\
 Představuje hodnotu pro čtení nebo zápis v laděném procesu.  
  
 [Hodnota ICorDebugValue2](icordebugvalue2-interface.md)\
 Rozšiřuje `ICorDebugValue` poskytovat podporu `ICorDebugType`pro .  
  
 [Rozhraní ICorDebugValue3](icordebugvalue3-interface.md)\
 Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" poskytovat podporu pro pole, která jsou větší než 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` poskytnout přístup ke konkrétním hodnotám.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugValue` pole.  
  
 [Rozhraní ICorDebugVariableHome](icordebugvariablehome-interface.md)\
 Představuje místní proměnnou nebo argument funkce.  
  
 [Rozhraní ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)\
 Poskytuje čítač pro místní proměnné a argumenty ve funkci.  
  
 [Rozhraní ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)\
 Načte informace o symbolu ladění pro proměnnou. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)\
 Poskytuje metody, které pomáhají při odvíjení zásobníku. **K dispozici pouze na nativním rozhraní .NET.**  
  
 [Rozhraní ICorPublish](icorpublish-interface.md)\
 Slouží jako obecné rozhraní pro procesy publikování.  
  
 [Rozhraní iCorpublishAppDomain](icorpublishappdomain-interface.md)\
 Představuje a poskytuje informace o aplikační doméně.  
  
 [Rozhraní ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)\
 Poskytuje metody, které procházejí `ICorPublishAppDomain` kolekcí objektů, které aktuálně existují v rámci procesu.  
  
 [Rozhraní ICorPublishEnum](icorpublishenum-interface.md)\
 Slouží jako abstraktní základ pro enumerátory publikování.  
  
 [Rozhraní ICorPublishProcess](icorpublishprocess-interface.md)\
 Poskytuje metody, které přistupují k informacím o procesu.  
  
 [Rozhraní ICorPublishProcessEnum](icorpublishprocessenum-interface.md)\
 Poskytuje metody, které procházejí `ICorPublishProcess` kolekcí objektů.  

 [Rozhraní ISOSDacInterface](isosdacinterface-interface.md)\
 Poskytuje pomocné metody pro `SOS`přístup k datům z aplikace .

 [Rozhraní IXCLRDataMethodDefinitionDefinition](ixclrdatamethoddefinition-interface.md)\
 Poskytuje metody pro dotazování na informace o definici metody.

 [Rozhraní IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)\
 Poskytuje metody pro dotazování na informace o instanci metody.

 [Rozhraní IXCLRDataModule](ixclrdatamodule-interface.md)\
 Poskytuje metody pro dotazování informací o načteném modulu.

 [Rozhraní IXCLRDataProcess](ixclrdataprocess-interface.md)\
 Poskytuje metody pro dotazování na informace o procesu.
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění kotříd](debugging-coclasses.md)\
 [Ladění globálních statických funkcí](debugging-global-static-functions.md)\
 [Ladění výčtů](debugging-enumerations.md)\
 [Ladicí struktury](debugging-structures.md)\
