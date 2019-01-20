---
title: Debugging – rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415959"
---
# <a name="debugging-interfaces"></a>Debugging – rozhraní
Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRDataEnumMemoryRegions – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.  
  
 [ICLRDataEnumMemoryRegionsCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 Poskytuje metodu zpětného volání pro `EnumMemoryRegions` k poskytnutí zprávy ladicímu programu, výsledek pokusu o výčet určité oblasti paměti.  
  
 [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Poskytuje metody pro interakci s cílovým procesem CLR.  
  
 [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Podtřída `ICLRDataTarget` vrstvou služeb přístupu k data, která se používá k manipulaci s oblastmi virtuální paměti v cílovém procesu.  
  
 [ICLRDataTarget3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Podtřída [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.  
  
 [ICLRDebugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
 [ICLRDebuggingLibraryProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 Zahrnuje [ProvideLibrary – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá rozhraní zpětného volání, které umožňuje knihovnám ladění specifickým pro verzi modulu runtime k vyhledání a načtení na požádání zprostředkovatele knihovny.  
  
 [ICLRMetadataLocator – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.  
  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.  
  
 [ICorDebugAppDomain – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Poskytuje metody pro ladění domén aplikace.  
  
 [ICorDebugAppDomain2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef. Toto rozhraní je rozšířením `ICorDebugAppDomain` rozhraní.  
  
 [ICorDebugAppDomain3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Poskytuje metody pro práci s [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v aplikační doméně. Toto rozhraní je rozšířením `ICorDebugAppDomain` a `ICorDebugAppDomain2` rozhraní.  
  
 [ICorDebugAppDomain4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Logicky rozšiřuje [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) získat objekt spravovaného z obálka volatelná aplikacemi COM rozhraní.  
  
 [ICorDebugAppDomainEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Poskytuje metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot počínaje na dalším místě ve výčtu.  
  
 [ICorDebugArrayValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Podtřída `ICorDebugHeapValue` , která představuje jednorozměrné nebo vícedimenzionální pole.  
  
 [ICorDebugAssembly – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Představuje sestavení.  
  
 [ICorDebugAssembly2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Představuje sestavení. Toto rozhraní je rozšířením `ICorDebugAssembly` rozhraní.  
  
 [ICorDebugAssembly3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Logicky rozšiřuje [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) rozhraní k poskytování podpory pro sestavení kontejneru a jejich obsažené sestavení. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugAssemblyEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugAssembly` pole.  
  
 [ICorDebugBlockingObjectEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Poskytuje enumerátor pro seznam [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
 [ICorDebugBoxValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Podtřída `ICorDebugHeapValue` představující objektu třídy zabalených hodnot.  
  
 [ICorDebugBreakpoint – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Představuje zarážku ve funkci nebo bod sledování na hodnotě.  
  
 [ICorDebugBreakpointEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugBreakpoint` pole.  
  
 [ICorDebugChain – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Představuje segment fyzického nebo logického zásobníku volání.  
  
 [ICorDebugChainEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugChain` pole.  
  
 [ICorDebugClass – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.  
  
 [ICorDebugClass2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>. Toto rozhraní rozšiřuje `ICorDebugClass`.  
  
 [ICorDebugCode – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
 [ICorDebugCode2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Poskytuje metody, které rozšiřují možnosti `ICorDebugCode`.  
  
 [ICorDebugCode3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Poskytuje metodu, která rozšiřuje [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) a [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) zadání informací o spravované návratové hodnotě.  
  
 [ICorDebugCode4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Poskytuje metodu, která umožňuje ladicí program, který výčet lokálních proměnných a argumentů funkce.  
  
 [ICorDebugCodeEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugCode` pole.  
  
 [ICorDebugComObjectValue – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Poskytuje metody pro načtení objektů z mezipaměti rozhraní.  
  
 [ICorDebugContext – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Představuje objekt kontextu. Toto rozhraní zatím nebylo implementováno.  
  
 [ICorDebugController – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Představuje rozsah buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu lze ovládat kontext.  
  
 [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
 [ICorDebugDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugDataTarget3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugEditAndContinueErrorInfo – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [ICorDebugEditAndContinueSnapshot – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [ICorDebugEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Slouží jako abstraktní základní rozhraní pro enumerátory ladění.  
  
 [ICorDebugErrorInfoEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [ICorDebugEval – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
 [ICorDebugEval2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Rozšiřuje `ICorDebugEval` k poskytování podpory pro obecné typy.  
  
 [ICorDebugExceptionDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu události výjimky. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugExceptionObjectCallStackEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.  
  
 [ICorDebugExceptionObjectValue – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Rozšiřuje [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) rozhraní pro poskytnutí informací o trasování zásobníku z objektu spravované výjimky.  
  
 [ICorDebugFrame – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Představuje snímek aktuálního zásobníku.  
  
 [ICorDebugFrameEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugFrame` pole.  
  
 [ICorDebugFunction – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Představuje spravovanou funkci nebo metodu.  
  
 [ICorDebugFunction2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Logicky rozšiřuje `ICorDebugFunction` a poskytuje podporu pro funkce pouze můj kód krokové ladění.  
  
 [ICorDebugFunction3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Logicky rozšiřuje [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) rozhraní pro žádost o ReJIT poskytují přístup ke kódu.  
  
 [ICorDebugFunctionBreakpoint – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.  
  
 [ICorDebugGCReferenceEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
 [ICorDebugGenericValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Podtřída `ICorDebugValue` , která platí pro všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
 [ICorDebugGuidToTypeEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a odpovídající `ICorDebugType` objekty.  
  
 [ICorDebugHandleValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Podtřída `ICorDebugReferenceValue` , která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.  
  
 [ICorDebugHeapEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Poskytuje enumerátor pro objekty na spravované haldě.  
  
 [ICorDebugHeapSegmentEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Poskytuje enumerátor pro oblasti paměti spravované haldy.  
  
 [ICorDebugHeapValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Podtřída `ICorDebugValue` , který představuje objekt, který byl shromážděn uvolňováním CLR.  
  
 [ICorDebugHeapValue2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 Rozšíření `ICorDebugHeapValue` , která poskytuje podporu pro popisovače modulu runtime.  
  
 [ICorDebugHeapValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Zpřístupní vlastnosti uzamčení sledování objektů.  
  
 [ICorDebugILCode – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Představuje segment kódu (IL intermediate language).  
  
 [ICorDebugILCode2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Logicky rozšiřuje [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) rozhraní poskytuje metody, které vracejí token pro místní proměnné podpis funkce a, která mapují profiler instrumentované (IL intermediate language) kompenzuje původní metody IL posuny.  
  
 [ICorDebugILFrame – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 Představuje rámec zásobníku kódu MSIL.  
  
 [ICorDebugILFrame2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Logické rozšíření `ICorDebugILFrame`.  
  
 [ICorDebugILFrame3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.  
  
 [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Poskytuje metody, které umožňují přístup k místní proměnné a kód v bloku zásobníku kódu (IL intermediate language). Parametr určuje, zda ladicí program má přístup k proměnné a kód přidaný v profileru ReJIT instrumentace.  
  
 [ICorDebugInstanceFieldSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Představuje informací symbolů ladění pro pole instance. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugInternalFrame – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Určuje typy rámců pro ladicí program.  
  
 [ICorDebugInternalFrame2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Poskytuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objekty.  
  
 [ICorDebugLoadedModule – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Poskytuje informace o u načteného modulu. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
 [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA). `ICorDebugManagedCallback2` je logickým rozšířením `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.  
  
 [ICorDebugMDA – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
 [ICorDebugMemoryBuffer – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Představuje vyrovnávací paměť v paměti. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Poskytuje informace o sloučené sestavení. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugMetaDataLocator – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Poskytuje informace metadat k ladicímu programu.  
  
 [ICorDebugModule – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).  
  
 [ICorDebugModule2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Slouží jako logické rozšíření pro `ICorDebugModule`.  
  
 [ICorDebugModule3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Vytvoří čtečku symbolů pro dynamický modul.  
  
 [ICorDebugModuleBreakpoint – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým modulům.  
  
 [ICorDebugModuleDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugModuleEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugModule` pole.  
  
 [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu proměnlivé datové cíle.  
  
 [ICorDebugNativeFrame – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Specializovaná implementace `ICorDebugFrame` pro nativní snímky.  
  
 [ICorDebugNativeFrame2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.  
  
 [ICorDebugObjectEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).  
  
 [ICorDebugObjectValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Podtřída `ICorDebugValue` , která představuje hodnotu, která obsahuje objekt.  
  
 [ICorDebugObjectValue2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.  
  
 [ICorDebugProcess – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Představuje proces, který spouští spravovaný kód.  
  
 [ICorDebugProcess2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Logické rozšíření `ICorDebugProcess`.  
  
 [ICorDebugProcess3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Řídí vlastní oznámení ladicího programu.  
  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní pro podporu přístupu ke spravované haldě, k poskytování informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z aplikace v místním mezipaměti nativních bitových kopií.  
  
 [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Logicky rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní k povolení funkcí, jako je například dekódování spravované ladění události, které jsou zakódovány nativní výjimka ladění událostí a rozdělení virtuální modulu. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugProcess7 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Poskytuje metodu, která nakonfiguruje ladicího programu pro zpracování aktualizace metadat v paměti v cílovém procesu.  
  
 [ICorDebugProcess8 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Logicky rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní pro povolení nebo zakázání určitých typů [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.  
  
 [ICorDebugProcessEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugProcess` pole.  
  
 [ICorDebugReferenceValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Podtřída `ICorDebugValue` podporující referenční typy.  
  
 [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.  
  
 [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.  
  
 [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.  
  
 [ICorDebugRuntimeUnwindableFrame – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
 [ICorDebugStackWalk – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
 [ICorDebugStaticFieldSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Představuje informací symbolů ladění pro statické pole. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugStepper – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
 [ICorDebugStepper2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Poskytuje podporu ladění Pouze můj kód (JMC).  
  
 [ICorDebugStepperEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugStepper` pole.  
  
 [ICorDebugStringValue – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Podtřída `ICorDebugHeapValue` aplikovaná na řetězcové hodnoty.  
  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Poskytuje metody, které slouží k načtení informací symbolů ladění. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugSymbolProvider2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Logicky rozšiřuje [icordebugsymbolprovider –](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní pro načtení informací o symbolu další ladění. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugThread – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Představuje vlákno v procesu. Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
 [ICorDebugThread2 – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Slouží jako logické rozšíření pro `ICorDebugThread`.  
  
 [ICorDebugThread3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Poskytuje vstupní bod, který [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.  
  
 [ICorDebugThread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 Poskytuje informace o blokování vlákna.  
  
 [ICorDebugThreadEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugThread` pole.  
  
 [ICorDebugType – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
 [ICorDebugType2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Rozšiřuje [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) rozhraní načtete identifikátor typu základního typu nebo komplexní typ (definovaný uživatelem).  
  
 [ICorDebugTypeEnum – rozhraní 1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugType` pole.  
  
 [ICorDebugUnmanagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.  
  
 "ICorDebugValue"  
 Představuje hodnotu pro čtení nebo zápis v laděném procesu.  
  
 Icordebugvalue2 "–"  
 Rozšiřuje `ICorDebugValue` k poskytování podpory pro `ICorDebugType`.  
  
 [ICorDebugValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" k poskytování podpory pro pole, která jsou větší než 2 GB.  
  
 Icordebugvaluebreakpoint "–"  
 Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým hodnotám.  
  
 Icordebugvalueenum "–"  
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugValue` pole.  
  
 [ICorDebugVariableHome – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Představuje místní proměnné nebo argumentu funkce.  
  
 [ICorDebugVariableHomeEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.  
  
 [ICorDebugVariableSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Načte informace o symbolu ladění pro proměnnou. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugVirtualUnwinder – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Poskytuje metody, které vám pomůžou odvíjení zásobníku. **K dispozici na pouze .NET Native.**  
  
 [ICorPublish – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Slouží jako obecné rozhraní pro procesy publikování.  
  
 [ICorPublishAppDomain – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Představuje a poskytuje informace o aplikační doméně.  
  
 [ICorPublishAppDomainEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Poskytuje metody, které procházejí kolekci `ICorPublishAppDomain` objekty, které momentálně existují v rámci procesu.  
  
 [ICorPublishEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Slouží jako abstraktní základ pro enumerátory publikování.  
  
 [ICorPublishProcess – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 Poskytuje metody, které přistupují k informacím o procesu.  
  
 [ICorPublishProcessEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Poskytuje metody, které procházejí kolekci `ICorPublishProcess` objekty.  

 [Rozhraní ISOSDacInterface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) poskytuje pomocné metody pro přístup k datům z `SOS`.

 [Rozhraní IXCLRDataMethodDefinition](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) poskytuje metody pro dotazování na informace o definici metody.
 
 [Rozhraní IXCLRDataMethodInstance](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) poskytuje metody pro dotazování na informace o metodu instance.
 
 [Rozhraní IXCLRDataModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) poskytuje metody pro dotazování na informace o u načteného modulu.
 
 [Rozhraní IXCLRDataProcess](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) poskytuje metody pro dotazování na informace o procesu.
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
