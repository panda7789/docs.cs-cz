---
title: Debugging – rozhraní
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698418"
---
# <a name="debugging-interfaces"></a>Debugging – rozhraní
Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\
 Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.  
  
 [ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\
 Poskytuje metodu zpětného volání pro `EnumMemoryRegions` k poskytnutí zprávy ladicímu programu, výsledek pokusu o výčet určité oblasti paměti.  
  
 [Iclrdatatarget – rozhraní](iclrdatatarget-interface.md)\
 Poskytuje metody pro interakci s cílovým procesem CLR.  
  
 [ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\
 Podtřída `ICLRDataTarget` vrstvou služeb přístupu k data, která se používá k manipulaci s oblastmi virtuální paměti v cílovém procesu.  
  
 [ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\
 Podtřída [iclrdatatarget2 –](iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.  
  
 [Iclrdebugging – rozhraní](iclrdebugging-interface.md)\
 Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
 [Iclrdebugginglibraryprovider – rozhraní](iclrdebugginglibraryprovider-interface.md)\
 Zahrnuje [ProvideLibrary – metoda](iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá rozhraní zpětného volání, které umožňuje knihovnám ladění specifickým pro verzi modulu runtime k vyhledání a načtení na požádání zprostředkovatele knihovny.  
  
 [ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\
 Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.  
  
 [Icordebug – rozhraní](icordebug-interface.md)\
 Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.  
  
 [ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\
 Poskytuje metody pro ladění domén aplikace.  
  
 [ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\
 Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef. Toto rozhraní je rozšířením `ICorDebugAppDomain` rozhraní.  
  
 [ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\
 Poskytuje metody pro práci s [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v aplikační doméně. Toto rozhraní je rozšířením `ICorDebugAppDomain` a `ICorDebugAppDomain2` rozhraní.  
  
 [ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\
 Logicky rozšiřuje [ICorDebugAppDomain](icordebugappdomain-interface.md) získat objekt spravovaného z obálka volatelná aplikacemi COM rozhraní.  
  
 [ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\
 Poskytuje metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot počínaje na dalším místě ve výčtu.  
  
 [ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\
 Podtřída `ICorDebugHeapValue` , která představuje jednorozměrné nebo vícedimenzionální pole.  
  
 [Icordebugassembly – rozhraní](icordebugassembly-interface.md)\
 Představuje sestavení.  
  
 [Icordebugassembly2 – rozhraní](icordebugassembly2-interface.md)\
 Představuje sestavení. Toto rozhraní je rozšířením `ICorDebugAssembly` rozhraní.  
  
 [Icordebugassembly3 – rozhraní](icordebugassembly3-interface.md)\
 Logicky rozšiřuje [ICorDebugAssembly](icordebugassembly-interface.md) rozhraní k poskytování podpory pro sestavení kontejneru a jejich obsažené sestavení. **K dispozici na pouze .NET Native.**  
  
 [Icordebugassemblyenum – rozhraní](icordebugassemblyenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugAssembly` pole.  
  
 [Icordebugblockingobjectenum – rozhraní](icordebugblockingobjectenum-interface.md)\
 Poskytuje enumerátor pro seznam [CorDebugBlockingObject](cordebugblockingobject-structure.md) struktury.  
  
 [Icordebugboxvalue – rozhraní](icordebugboxvalue-interface.md)\
 Podtřída `ICorDebugHeapValue` představující objektu třídy zabalených hodnot.  
  
 [Icordebugbreakpoint – rozhraní](icordebugbreakpoint-interface.md)\
 Představuje zarážku ve funkci nebo bod sledování na hodnotě.  
  
 [Icordebugbreakpointenum – rozhraní](icordebugbreakpointenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugBreakpoint` pole.  
  
 [Icordebugchain – rozhraní](icordebugchain-interface.md)\
 Představuje segment fyzického nebo logického zásobníku volání.  
  
 [Icordebugchainenum – rozhraní](icordebugchainenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugChain` pole.  
  
 [Icordebugclass – rozhraní](icordebugclass-interface.md)\
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.  
  
 [Icordebugclass2 – rozhraní](icordebugclass2-interface.md)\
 Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>. Toto rozhraní rozšiřuje `ICorDebugClass`.  
  
 [Icordebugcode – rozhraní](icordebugcode-interface1.md)\
 Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
 [Icordebugcode2 – rozhraní](icordebugcode2-interface.md)\
 Poskytuje metody, které rozšiřují možnosti `ICorDebugCode`.  
  
 [Icordebugcode3 – rozhraní](icordebugcode3-interface.md)\
 Poskytuje metodu, která rozšiřuje [ICorDebugCode](icordebugcode-interface1.md) a [ICorDebugCode2](icordebugcode2-interface.md) zadání informací o spravované návratové hodnotě.  
  
 [Icordebugcode4 – rozhraní](icordebugcode4-interface.md)\
 Poskytuje metodu, která umožňuje ladicí program, který výčet lokálních proměnných a argumentů funkce.  
  
 [Icordebugcodeenum – rozhraní](icordebugcodeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugCode` pole.  
  
 [ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\
 Poskytuje metody pro načtení objektů z mezipaměti rozhraní.  
  
 [ICorDebugContext Interface](icordebugcontext-interface.md)\
 Představuje objekt kontextu. Toto rozhraní zatím nebylo implementováno.  
  
 [Icordebugcontroller – rozhraní](icordebugcontroller-interface.md)\
 Představuje rozsah buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu lze ovládat kontext.  
  
 [Icordebugdatatarget – rozhraní](icordebugdatatarget-interface.md)\
 Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
 [ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\
 Logicky rozšiřuje [icordebugdatatarget –](icordebugdatatarget-interface.md) rozhraní. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\
 Logicky rozšiřuje [icordebugdatatarget –](icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly. **K dispozici na pouze .NET Native.**  
  
 [Icordebugdebugevent – rozhraní](icordebugdebugevent-interface.md)\
 Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [Icordebugenum – rozhraní](icordebugenum-interface1.md)\
 Slouží jako abstraktní základní rozhraní pro enumerátory ladění.  
  
 [Icordebugerrorinfoenum – rozhraní](icordebugerrorinfoenum-interface.md)\
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 [Icordebugeval – rozhraní](icordebugeval-interface.md)\
 Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
 [Icordebugeval2 – rozhraní](icordebugeval2-interface.md)\
 Rozšiřuje `ICorDebugEval` k poskytování podpory pro obecné typy.  
  
 [Icordebugexceptiondebugevent – rozhraní](icordebugexceptiondebugevent-interface.md)\
 Rozšiřuje [ICorDebugDebugEvent](icordebugdebugevent-interface.md) rozhraní pro podporu události výjimky. **K dispozici na pouze .NET Native.**  
  
 [Icordebugexceptionobjectcallstackenum – rozhraní](icordebugexceptionobjectcallstackenum-interface.md)\
 Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.  
  
 [ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\
 Rozšiřuje [ICorDebugObjectValue](icordebugobjectvalue-interface.md) rozhraní pro poskytnutí informací o trasování zásobníku z objektu spravované výjimky.  
  
 [Icordebugframe – rozhraní](icordebugframe-interface.md)\
 Představuje snímek aktuálního zásobníku.  
  
 [Icordebugframeenum – rozhraní](icordebugframeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugFrame` pole.  
  
 [Icordebugfunction – rozhraní](icordebugfunction-interface1.md)\
 Představuje spravovanou funkci nebo metodu.  
  
 [Icordebugfunction2 – rozhraní](icordebugfunction2-interface.md)\
 Logicky rozšiřuje `ICorDebugFunction` a poskytuje podporu pro funkce pouze můj kód krokové ladění.  
  
 [Icordebugfunction3 – rozhraní](icordebugfunction3-interface.md)\
 Logicky rozšiřuje [ICorDebugFunction](icordebugfunction-interface1.md) rozhraní pro žádost o ReJIT poskytují přístup ke kódu.  
  
 [Icordebugfunctionbreakpoint – rozhraní](icordebugfunctionbreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.  
  
 [Icordebuggcreferenceenum – rozhraní](icordebuggcreferenceenum-interface.md)\
 Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
 [Icordebuggenericvalue – rozhraní](icordebuggenericvalue-interface.md)\
 Podtřída `ICorDebugValue` , která platí pro všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
 [Icordebugguidtotypeenum – rozhraní](icordebugguidtotypeenum-interface.md)\
 Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a odpovídající `ICorDebugType` objekty.  
  
 [Icordebughandlevalue – rozhraní](icordebughandlevalue-interface.md)\
 Podtřída `ICorDebugReferenceValue` , která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.  
  
 [Icordebugheapenum – rozhraní](icordebugheapenum-interface.md)\
 Poskytuje enumerátor pro objekty na spravované haldě.  
  
 [Icordebugheapsegmentenum – rozhraní](icordebugheapsegmentenum-interface.md)\
 Poskytuje enumerátor pro oblasti paměti spravované haldy.  
  
 [Icordebugheapvalue – rozhraní](icordebugheapvalue-interface.md)\
 Podtřída `ICorDebugValue` , který představuje objekt, který byl shromážděn uvolňováním CLR.  
  
 [ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\
 Rozšíření `ICorDebugHeapValue` , která poskytuje podporu pro popisovače modulu runtime.  
  
 [ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\
 Zpřístupní vlastnosti uzamčení sledování objektů.  
  
 [Icordebugilcode – rozhraní](icordebugilcode-interface.md)\
 Představuje segment kódu (IL intermediate language).  
  
 [Icordebugilcode2 – rozhraní](icordebugilcode2-interface.md)\
 Logicky rozšiřuje [ICorDebugILCode](icordebugilcode-interface.md) rozhraní poskytuje metody, které vracejí token pro místní proměnné podpis funkce a, která mapují profiler instrumentované (IL intermediate language) kompenzuje původní metody IL posuny.  
  
 [Icordebugilframe – rozhraní](icordebugilframe-interface.md)\
 Představuje rámec zásobníku kódu MSIL.  
  
 [Icordebugilframe2 – rozhraní](icordebugilframe2-interface.md)\
 Logické rozšíření `ICorDebugILFrame`.  
  
 [Icordebugilframe3 – rozhraní](icordebugilframe3-interface.md)\
 Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.  
  
 [Icordebugilframe4 – rozhraní](icordebugilframe4-interface.md)\
 Poskytuje metody, které umožňují přístup k místní proměnné a kód v bloku zásobníku kódu (IL intermediate language). Parametr určuje, zda ladicí program má přístup k proměnné a kód přidaný v profileru ReJIT instrumentace.  
  
 [ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\
 Představuje informací symbolů ladění pro pole instance. **K dispozici na pouze .NET Native.**  
  
 [Icordebuginternalframe – rozhraní](icordebuginternalframe-interface.md)\
 Určuje typy rámců pro ladicí program.  
  
 [Icordebuginternalframe2 – rozhraní](icordebuginternalframe2-interface.md)\
 Poskytuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k [ICorDebugFrame](icordebugframe-interface.md) objekty.  
  
 [Icordebugloadedmodule – rozhraní](icordebugloadedmodule-interface.md)\
 Poskytuje informace o u načteného modulu. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\
 Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
 [ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\
 Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA). `ICorDebugManagedCallback2` je logickým rozšířením `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\
 Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.  
  
 [Icordebugmda – rozhraní](icordebugmda-interface.md)\
 Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
 [ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\
 Představuje vyrovnávací paměť v paměti. **K dispozici na pouze .NET Native.**  
  
 [Icordebugmergedassemblyrecord – rozhraní](icordebugmergedassemblyrecord-interface.md)\
 Poskytuje informace o sloučené sestavení. **K dispozici na pouze .NET Native.**  
  
 [ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\
 Poskytuje informace metadat k ladicímu programu.  
  
 [ICorDebugModule Interface](icordebugmodule-interface.md)\
 Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).  
  
 [ICorDebugModule2 Interface](icordebugmodule2-interface.md)\
 Slouží jako logické rozšíření pro `ICorDebugModule`.  
  
 [ICorDebugModule3 Interface](icordebugmodule3-interface.md)\
 Vytvoří čtečku symbolů pro dynamický modul.  
  
 [ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým modulům.  
  
 [Icordebugmoduledebugevent – rozhraní](icordebugmoduledebugevent-interface.md)\
 Rozšiřuje [ICorDebugDebugEvent](icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu. **K dispozici na pouze .NET Native.**  
  
 [Icordebugmoduleenum – rozhraní](icordebugmoduleenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugModule` pole.  
  
 [ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\
 Rozšiřuje [icordebugdatatarget –](icordebugdatatarget-interface.md) rozhraní pro podporu proměnlivé datové cíle.  
  
 [Icordebugnativeframe – rozhraní](icordebugnativeframe-interface.md)\
 Specializovaná implementace `ICorDebugFrame` pro nativní snímky.  
  
 [Icordebugnativeframe2 – rozhraní](icordebugnativeframe2-interface.md)\
 Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.  
  
 [Icordebugobjectenum – rozhraní](icordebugobjectenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).  
  
 [Icordebugobjectvalue – rozhraní](icordebugobjectvalue-interface.md)\
 Podtřída `ICorDebugValue` , která představuje hodnotu, která obsahuje objekt.  
  
 [Icordebugobjectvalue2 – rozhraní](icordebugobjectvalue2-interface.md)\
 Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.  
  
 [Icordebugprocess – rozhraní](icordebugprocess-interface.md)\
 Představuje proces, který spouští spravovaný kód.  
  
 [Icordebugprocess2 – rozhraní](icordebugprocess2-interface1.md)\
 Logické rozšíření `ICorDebugProcess`.  
  
 [Icordebugprocess3 – rozhraní](icordebugprocess3-interface.md)\
 Řídí vlastní oznámení ladicího programu.

 [ICorDebugProcess4 rozhraní](icordebugprocess4-interface.md)\
 Poskytuje podporu pro mimo proces řízení provádění.
  
 [Icordebugprocess5 – rozhraní](icordebugprocess5-interface.md)\
 Rozšiřuje [ICorDebugProcess](icordebugprocess-interface.md) rozhraní pro podporu přístupu ke spravované haldě, k poskytování informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z aplikace v místním mezipaměti nativních bitových kopií.  
  
 [Icordebugprocess6 – rozhraní](icordebugprocess6-interface.md)\
 Logicky rozšiřuje [ICorDebugProcess](icordebugprocess-interface.md) rozhraní k povolení funkcí, jako je například dekódování spravované ladění události, které jsou zakódovány nativní výjimka ladění událostí a rozdělení virtuální modulu. **K dispozici na pouze .NET Native.**  
  
 [Icordebugprocess7 – rozhraní](icordebugprocess7-interface.md)\
 Poskytuje metodu, která nakonfiguruje ladicího programu pro zpracování aktualizace metadat v paměti v cílovém procesu.  
  
 [Icordebugprocess8 – rozhraní](icordebugprocess8-interface.md)\
 Logicky rozšiřuje [ICorDebugProcess](icordebugprocess-interface.md) rozhraní pro povolení nebo zakázání určitých typů [icordebugmanagedcallback2 –](icordebugmanagedcallback2-interface.md) zpětných volání výjimky.  
  
 [Icordebugprocessenum – rozhraní](icordebugprocessenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugProcess` pole.  
  
 [Icordebugreferencevalue – rozhraní](icordebugreferencevalue-interface.md)\
 Podtřída `ICorDebugValue` podporující referenční typy.  
  
 [Icordebugregisterset – rozhraní](icordebugregisterset-interface.md)\
 Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
 [Icordebugregisterset2 – rozhraní](icordebugregisterset2-interface.md)\
 Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.  
  
 [Icordebugremote – rozhraní](icordebugremote-interface.md)\
 Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.  
  
 [Icordebugremotetarget – rozhraní](icordebugremotetarget-interface.md)\
 Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.  
  
 [ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\
 Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
 [Icordebugstackwalk – rozhraní](icordebugstackwalk-interface.md)\
 Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
 [Icordebugstaticfieldsymbol – rozhraní](icordebugstaticfieldsymbol-interface.md)\
 Představuje informací symbolů ladění pro statické pole. **K dispozici na pouze .NET Native.**  
  
 [Icordebugstepper – rozhraní](icordebugstepper-interface.md)\
 Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
 [Icordebugstepper2 – rozhraní](icordebugstepper2-interface1.md)\
 Poskytuje podporu ladění Pouze můj kód (JMC).  
  
 [Icordebugstepperenum – rozhraní](icordebugstepperenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugStepper` pole.  
  
 [ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\
 Podtřída `ICorDebugHeapValue` aplikovaná na řetězcové hodnoty.  
  
 [Icordebugsymbolprovider – rozhraní](icordebugsymbolprovider-interface.md)\
 Poskytuje metody, které slouží k načtení informací symbolů ladění. **K dispozici na pouze .NET Native.**  
  
 [Icordebugsymbolprovider2 – rozhraní](icordebugsymbolprovider2-interface.md)\
 Logicky rozšiřuje [icordebugsymbolprovider –](icordebugsymbolprovider-interface.md) rozhraní pro načtení informací o symbolu další ladění. **K dispozici na pouze .NET Native.**  
  
 [Icordebugthread – rozhraní](icordebugthread-interface.md)\
 Představuje vlákno v procesu. Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
 [Icordebugthread2 – rozhraní](icordebugthread2-interface.md)\
 Slouží jako logické rozšíření pro `ICorDebugThread`.  
  
 [Icordebugthread3 – rozhraní](icordebugthread3-interface.md)\
 Poskytuje vstupní bod, který [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.  
  
 [Icordebugthread4 – rozhraní](icordebugthread4-interface.md)\
 Poskytuje informace o blokování vlákna.  
  
 [Icordebugthreadenum – rozhraní](icordebugthreadenum-interface1.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugThread` pole.  
  
 [Icordebugtype – rozhraní](icordebugtype-interface.md)\
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
 [Icordebugtype2 – rozhraní](icordebugtype2-interface.md)\
 Rozšiřuje [ICorDebugType](icordebugtype-interface.md) rozhraní načtete identifikátor typu základního typu nebo komplexní typ (definovaný uživatelem).  
  
 [Icordebugtypeenum – rozhraní](icordebugtypeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugType` pole.  
  
 [ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\
 Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Představuje hodnotu pro čtení nebo zápis v laděném procesu.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Rozšiřuje `ICorDebugValue` k poskytování podpory pro `ICorDebugType`.  
  
 [Icordebugvalue3 – rozhraní](icordebugvalue3-interface.md)\
 Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" k poskytování podpory pro pole, která jsou větší než 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým hodnotám.  
  
 [Icordebugvalueenum –](icordebugvalueenum-interface.md)\
 Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugValue` pole.  
  
 [Icordebugvariablehome – rozhraní](icordebugvariablehome-interface.md)\
 Představuje místní proměnné nebo argumentu funkce.  
  
 [Icordebugvariablehomeenum – rozhraní](icordebugvariablehomeenum-interface.md)\
 Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.  
  
 [ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\
 Načte informace o symbolu ladění pro proměnnou. **K dispozici na pouze .NET Native.**  
  
 [Icordebugvirtualunwinder – rozhraní](icordebugvirtualunwinder-interface.md)\
 Poskytuje metody, které vám pomůžou odvíjení zásobníku. **K dispozici na pouze .NET Native.**  
  
 [Icorpublish – rozhraní](icorpublish-interface.md)\
 Slouží jako obecné rozhraní pro procesy publikování.  
  
 [Icorpublishappdomain – rozhraní](icorpublishappdomain-interface.md)\
 Představuje a poskytuje informace o aplikační doméně.  
  
 [Icorpublishappdomainenum – rozhraní](icorpublishappdomainenum-interface.md)\
 Poskytuje metody, které procházejí kolekci `ICorPublishAppDomain` objekty, které momentálně existují v rámci procesu.  
  
 [Icorpublishenum – rozhraní](icorpublishenum-interface.md)\
 Slouží jako abstraktní základ pro enumerátory publikování.  
  
 [Icorpublishprocess – rozhraní](icorpublishprocess-interface.md)\
 Poskytuje metody, které přistupují k informacím o procesu.  
  
 [Icorpublishprocessenum – rozhraní](icorpublishprocessenum-interface.md)\
 Poskytuje metody, které procházejí kolekci `ICorPublishProcess` objekty.  

 [ISOSDacInterface rozhraní](isosdacinterface-interface.md)\
 Poskytuje pomocné metody pro přístup k datům z `SOS`.

 [IXCLRDataMethodDefinition rozhraní](ixclrdatamethoddefinition-interface.md)\
 Poskytuje metody pro dotazování na informace o definici metody.
 
 [IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\
 Poskytuje metody pro dotazování na informace o metodu instance.
 
 [IXCLRDataModule Interface](ixclrdatamodule-interface.md)\
 Poskytuje metody pro dotazování na informace o u načteného modulu.
 
 [IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\
 Poskytuje metody pro dotazování na informace o procesu.
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění tříd typu coclass](debugging-coclasses.md)\
 [Globální statické funkce ladění](debugging-global-static-functions.md)\
 [Výčty pro ladění](debugging-enumerations.md)\
 [Struktury pro ladění](debugging-structures.md)\
