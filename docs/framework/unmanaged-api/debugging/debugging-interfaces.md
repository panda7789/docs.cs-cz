---
title: Debugging – rozhraní
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097194"
---
# <a name="debugging-interfaces"></a>Debugging – rozhraní
Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 \ [rozhraní ICLRDataEnumMemoryRegions –](iclrdataenummemoryregions-interface.md)
 Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.  
  
 \ [rozhraní ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md)
 Poskytuje metodu zpětného volání pro `EnumMemoryRegions` pro hlášení ladicímu programu, výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.  
  
 \ [rozhraní ICLRDataTarget](iclrdatatarget-interface.md)
 Poskytuje metody pro interakci s cílovým procesem CLR.  
  
 \ [rozhraní ICLRDataTarget2](iclrdatatarget2-interface.md)
 Podtřída `ICLRDataTarget`, kterou vrstva služeb Data Access používá ke zpracování oblastí virtuální paměti v cílovém procesu.  
  
 \ [rozhraní ICLRDataTarget3](iclrdatatarget3-interface.md)
 Podtřída [ICLRDataTarget2](iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.  
  
 \ [rozhraní ICLRDebugging](iclrdebugging-interface.md)
 Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
 \ [rozhraní ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)
 Obsahuje metodu [metody ProvideLibrary –](iclrdebugginglibraryprovider-providelibrary-method.md) , která získá rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění pro Common Language Runtime v konkrétní verzi.  
  
 \ [rozhraní ICLRMetadataLocator –](iclrmetadatalocator-interface.md)
 Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.  
  
 \ [rozhraní ICorDebug](icordebug-interface.md)
 Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.  
  
 \ [rozhraní ICorDebugAppDomain](icordebugappdomain-interface.md)
 Poskytuje metody pro ladění domén aplikace.  
  
 \ [rozhraní ICorDebugAppDomain2](icordebugappdomain2-interface.md)
 Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef. Toto rozhraní je rozšířením rozhraní `ICorDebugAppDomain`.  
  
 \ [rozhraní ICorDebugAppDomain3](icordebugappdomain3-interface.md)
 Poskytuje metody pro práci s typy prostředí Windows Runtime v doméně aplikace. Toto rozhraní je rozšířením rozhraní `ICorDebugAppDomain` a `ICorDebugAppDomain2`.  
  
 \ [rozhraní ICorDebugAppDomain4](icordebugappdomain4-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugAppDomain](icordebugappdomain-interface.md) , aby získala spravovaný objekt z obálky s přípravnou modelem COM.  
  
 \ [rozhraní ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)
 Poskytuje metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot od dalšího umístění ve výčtu.  
  
 \ [rozhraní ICorDebugArrayValue](icordebugarrayvalue-interface.md)
 Podtřída `ICorDebugHeapValue`, která představuje jednorozměrné nebo multidimenzionální pole.  
  
 \ [rozhraní ICorDebugAssembly](icordebugassembly-interface.md)
 Představuje sestavení.  
  
 \ [rozhraní ICorDebugAssembly2](icordebugassembly2-interface.md)
 Představuje sestavení. Toto rozhraní je rozšířením rozhraní `ICorDebugAssembly`.  
  
 \ [rozhraní ICorDebugAssembly3](icordebugassembly3-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugAssembly](icordebugassembly-interface.md) , aby poskytovala podporu pro sestavení kontejneru a jejich obsažená sestavení. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugAssembly` polí.  
  
 \ [rozhraní ICorDebugBlockingObjectEnum –](icordebugblockingobjectenum-interface.md)
 Poskytuje enumerátor pro seznam struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .  
  
 \ [rozhraní ICorDebugBoxValue](icordebugboxvalue-interface.md)
 Podtřída `ICorDebugHeapValue`, která představuje zabalený objekt třídy hodnot.  
  
 \ [rozhraní ICorDebugBreakpoint](icordebugbreakpoint-interface.md)
 Představuje zarážku ve funkci nebo bod sledování na hodnotě.  
  
 \ [rozhraní ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugBreakpoint` polí.  
  
 \ [rozhraní ICorDebugChain](icordebugchain-interface.md)
 Představuje segment fyzického nebo logického zásobníku volání.  
  
 \ [rozhraní ICorDebugChainEnum](icordebugchainenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugChain` polí.  
  
 \ [rozhraní ICorDebugClass](icordebugclass-interface.md)
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.  
  
 \ [rozhraní ICorDebugClass2](icordebugclass2-interface.md)
 Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>. Toto rozhraní rozšiřuje `ICorDebugClass`.  
  
 \ [rozhraní ICorDebugCode](icordebugcode-interface1.md)
 Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
 \ [rozhraní ICorDebugCode2](icordebugcode2-interface.md)
 Poskytuje metody, které rozšiřuje možnosti `ICorDebugCode`.  
  
 \ [rozhraní ICorDebugCode3](icordebugcode3-interface.md)
 Poskytuje metodu, která rozšiřuje [ICorDebugCode](icordebugcode-interface1.md) a [ICorDebugCode2](icordebugcode2-interface.md) a poskytuje informace o spravované návratové hodnotě.  
  
 \ [rozhraní ICorDebugCode4](icordebugcode4-interface.md)
 Poskytuje metodu, která umožňuje ladicímu programu vytvořit výčet místních proměnných a argumentů ve funkci.  
  
 \ [rozhraní ICorDebugCodeEnum](icordebugcodeenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugCode` polí.  
  
 \ [rozhraní ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)
 Poskytuje metody pro načtení objektů z mezipaměti rozhraní.  
  
 \ [rozhraní ICorDebugContext –](icordebugcontext-interface.md)
 Představuje objekt kontextu. Toto rozhraní zatím nebylo implementováno.  
  
 \ [rozhraní ICorDebugController](icordebugcontroller-interface.md)
 Představuje obor, buď <xref:System.Diagnostics.Process>, nebo <xref:System.AppDomain>, ve kterém lze ovládat kontext provádění kódu.  
  
 \ [rozhraní ICorDebugDataTarget](icordebugdatatarget-interface.md)
 Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
 \ [rozhraní ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) . **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugDataTarget3](icordebugdatatarget3-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) , aby poskytovala informace o načtených modulech. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugDebugEvent](icordebugdebugevent-interface.md)
 Definuje základní rozhraní, ze kterého jsou odvozeny všechny události `ICorDebug` ladění. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 \ [rozhraní ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 \ [rozhraní ICorDebugEnum](icordebugenum-interface1.md)
 Slouží jako abstraktní základní rozhraní pro enumerátory ladění.  
  
 \ [rozhraní ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)
 Zastaralé. Toto rozhraní nepoužívejte.  
  
 \ [rozhraní ICorDebugEval](icordebugeval-interface.md)
 Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
 \ [rozhraní ICorDebugEval2](icordebugeval2-interface.md)
 Rozšiřuje `ICorDebugEval` pro zajištění podpory pro obecné typy.  
  
 \ [rozhraní ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
 Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí výjimek. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)
 Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.  
  
 \ [rozhraní ICorDebugExceptionObjectValue –](icordebugexceptionobjectvalue-interface.md)
 Rozšiřuje rozhraní [ICorDebugObjectValue](icordebugobjectvalue-interface.md) pro poskytnutí informací o trasování zásobníku z objektu spravované výjimky.  
  
 \ [rozhraní ICorDebugFrame](icordebugframe-interface.md)
 Představuje snímek aktuálního zásobníku.  
  
 \ [rozhraní ICorDebugFrameEnum](icordebugframeenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugFrame` polí.  
  
 \ [rozhraní ICorDebugFunction](icordebugfunction-interface1.md)
 Představuje spravovanou funkci nebo metodu.  
  
 \ [rozhraní ICorDebugFunction2](icordebugfunction2-interface.md)
 Logicky rozšiřuje `ICorDebugFunction` a poskytuje podporu pro Pouze můj kód krokování prostřednictvím ladění.  
  
 \ [rozhraní ICorDebugFunction3](icordebugfunction3-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugFunction](icordebugfunction-interface1.md) a poskytuje přístup k kódu z požadavku ReJIT.  
  
 \ [rozhraní ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)
 Rozšiřuje `ICorDebugBreakpoint` o podporu zarážek v rámci funkcí.  
  
 \ [rozhraní ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md)
 Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
 \ [rozhraní ICorDebugGenericValue](icordebuggenericvalue-interface.md)
 Podtřída `ICorDebugValue`, která se vztahuje na všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
 \ [rozhraní ICorDebugGuidToTypeEnum –](icordebugguidtotypeenum-interface.md)
 Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a odpovídající objekty `ICorDebugType`.  
  
 \ [rozhraní ICorDebugHandleValue](icordebughandlevalue-interface.md)
 Podtřída `ICorDebugReferenceValue` reprezentující referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.  
  
 \ [rozhraní ICorDebugHeapEnum –](icordebugheapenum-interface.md)
 Poskytuje enumerátor pro objekty na spravované haldě.  
  
 \ [rozhraní ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md)
 Poskytuje enumerátor pro oblasti paměti spravované haldy.  
  
 \ [rozhraní ICorDebugHeapValue](icordebugheapvalue-interface.md)
 Podtřída `ICorDebugValue`, která představuje objekt, který byl shromážděn systémem uvolňování paměti CLR.  
  
 \ [rozhraní ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)
 Rozšíření `ICorDebugHeapValue`, které poskytuje podporu pro obslužné rutiny modulu runtime.  
  
 \ [rozhraní ICorDebugHeapValue3](icordebugheapvalue3-interface.md)
 Zpřístupní vlastnosti uzamčení sledování objektů.  
  
 \ [rozhraní ICorDebugILCode](icordebugilcode-interface.md)
 Představuje segment kódu zprostředkujícího jazyka (IL).  
  
 \ [rozhraní ICorDebugILCode2](icordebugilcode2-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugILCode](icordebugilcode-interface.md) a poskytuje metody, které vracejí token pro místní proměnnou funkce a které mapují posuny instrumentované zprostředkujícího jazyka (IL) profileru na původní posunutí metody Il.  
  
 \ [rozhraní ICorDebugILFrame](icordebugilframe-interface.md)
 Představuje rámec zásobníku kódu MSIL.  
  
 \ [rozhraní ICorDebugILFrame2](icordebugilframe2-interface.md)
 Logické rozšíření `ICorDebugILFrame`.  
  
 \ [rozhraní ICorDebugILFrame3](icordebugilframe3-interface.md)
 Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.  
  
 \ [rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)
 Poskytuje metody, které umožňují přístup k místním proměnným a kódu v bloku rozhraní IL (Intermediate Language). Parametr určuje, jestli má ladicí program přístup k proměnným a kódu přidanému v profileru ReJIT instrumentace.  
  
 \ [rozhraní ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)
 Představuje informace o symbolech ladění pro pole instance. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugInternalFrame](icordebuginternalframe-interface.md)
 Určuje typy rámců pro ladicí program.  
  
 \ [rozhraní ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)
 Obsahuje informace o vnitřních rámečcích, včetně adresy zásobníku a pozice ve vztahu k [ICorDebugFrame](icordebugframe-interface.md) objektům.  
  
 \ [rozhraní metoda ICorDebugLoadedModule](icordebugloadedmodule-interface.md)
 Poskytuje informace o načteném modulu. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
 Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
 \ [rozhraní ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)
 Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA). `ICorDebugManagedCallback2` je logické rozšíření `ICorDebugManagedCallback`.  
  
 \ [rozhraní ICorDebugManagedCallback3 –](icordebugmanagedcallback3-interface.md)
 Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.  
  
 \ [rozhraní ICorDebugMDA](icordebugmda-interface.md)
 Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
 \ [rozhraní ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
 Představuje vyrovnávací paměť v paměti. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
 Poskytuje informace o sloučeném sestavení. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugMetaDataLocator –](icordebugmetadatalocator-interface.md)
 Poskytuje informace metadat k ladicímu programu.  
  
 \ [rozhraní ICorDebugModule](icordebugmodule-interface.md)
 Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).  
  
 \ [rozhraní ICorDebugModule2](icordebugmodule2-interface.md)
 Slouží jako logické rozšíření `ICorDebugModule`.  
  
 \ [rozhraní ICorDebugModule3](icordebugmodule3-interface.md)
 Vytvoří čtečku symbolů pro dynamický modul.  
  
 \ [rozhraní ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)
 Rozšiřuje `ICorDebugBreakpoint` o poskytnutí přístupu ke konkrétním modulům.  
  
 \ [rozhraní ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)
 Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugModuleEnum](icordebugmoduleenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugModule` polí.  
  
 \ [rozhraní ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)
 Rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.  
  
 \ [rozhraní ICorDebugNativeFrame](icordebugnativeframe-interface.md)
 Specializovaná implementace `ICorDebugFrame` používaná pro nativní rámce.  
  
 \ [rozhraní ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)
 Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.  
  
 \ [rozhraní ICorDebugObjectEnum](icordebugobjectenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet polí objektů podle jejich relativních virtuálních adres (RVA).  
  
 \ [rozhraní ICorDebugObjectValue](icordebugobjectvalue-interface.md)
 Podtřída `ICorDebugValue`, která představuje hodnotu, která obsahuje objekt.  
  
 \ [rozhraní ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)
 Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.  
  
 \ [rozhraní ICorDebugProcess](icordebugprocess-interface.md)
 Představuje proces, který spouští spravovaný kód.  
  
 \ [rozhraní ICorDebugProcess2](icordebugprocess2-interface1.md)
 Logické rozšíření `ICorDebugProcess`.  
  
 \ [rozhraní ICorDebugProcess3 –](icordebugprocess3-interface.md)
 Řídí vlastní oznámení ladicího programu.

 \ [rozhraní ICorDebugProcess4](icordebugprocess4-interface.md)
 Poskytuje podporu pro vzdálené řízení spouštění procesů.
  
 \ [rozhraní ICorDebugProcess5](icordebugprocess5-interface.md)
 Rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) pro podporu přístupu ke spravované haldě, k poskytnutí informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z místní mezipaměti nativních bitových kopií aplikace.  
  
 \ [rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) a povoluje funkce jako dekódování spravovaných událostí ladění, které jsou zakódované v nativních událostech ladění výjimek a rozdělování virtuálních modulů. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugProcess7](icordebugprocess7-interface.md)
 Poskytuje metodu, která konfiguruje ladicí program pro zpracování aktualizací metadat v paměti v cílovém procesu.  
  
 \ [rozhraní ICorDebugProcess8](icordebugprocess8-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) a povoluje nebo zakazuje určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
 \ [rozhraní ICorDebugProcessEnum](icordebugprocessenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugProcess` polí.  
  
 \ [rozhraní ICorDebugReferenceValue](icordebugreferencevalue-interface.md)
 Podtřída `ICorDebugValue`, která podporuje typy odkazů.  
  
 \ [rozhraní ICorDebugRegisterSet](icordebugregisterset-interface.md)
 Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
 \ [rozhraní ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
 Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.  
  
 \ [rozhraní ICorDebugRemote](icordebugremote-interface.md)
 Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.  
  
 \ [rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md)
 Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.  
  
 \ [rozhraní ICorDebugRuntimeUnwindableFrame –](icordebugruntimeunwindableframe-interface.md)
 Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
 \ [rozhraní ICorDebugStackWalk](icordebugstackwalk-interface.md)
 Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
 \ [rozhraní ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)
 Představuje informace o symbolech ladění pro statické pole. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugStepper](icordebugstepper-interface.md)
 Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
 \ [rozhraní ICorDebugStepper2](icordebugstepper2-interface1.md)
 Poskytuje podporu ladění Pouze můj kód (JMC).  
  
 \ [rozhraní ICorDebugStepperEnum](icordebugstepperenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugStepper` polí.  
  
 \ [rozhraní ICorDebugStringValue](icordebugstringvalue-interface.md)
 Podtřída `ICorDebugHeapValue`, která se vztahuje na řetězcové hodnoty.  
  
 \ [rozhraní ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
 Poskytuje metody, které lze použít k načtení informací o symbolech ladění. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)
 Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) a načítá Další informace o symbolech ladění. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugThread](icordebugthread-interface.md)
 Představuje vlákno v procesu. Doba životnosti `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
 \ [rozhraní ICorDebugThread2](icordebugthread2-interface.md)
 Slouží jako logické rozšíření `ICorDebugThread`.  
  
 \ [rozhraní ICorDebugThread3](icordebugthread3-interface.md)
 Poskytuje vstupní bod pro [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.  
  
 \ [rozhraní ICorDebugThread4](icordebugthread4-interface.md)
 Poskytuje informace o blokování vlákna.  
  
 \ [rozhraní ICorDebugThreadEnum](icordebugthreadenum-interface1.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugThread` polí.  
  
 \ [rozhraní ICorDebugType](icordebugtype-interface.md)
 Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
 \ [rozhraní ICorDebugType2](icordebugtype2-interface.md)
 Rozšiřuje rozhraní [ICorDebugType](icordebugtype-interface.md) , aby získal identifikátor typu základního typu nebo komplexního (uživatelsky definovaného) typu.  
  
 \ [rozhraní ICorDebugTypeEnum](icordebugtypeenum-interface.md)
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugType` polí.  
  
 \ [rozhraní ICorDebugUnmanagedCallback –](icordebugunmanagedcallback-interface.md)
 Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Představuje hodnotu pro čtení nebo zápis v laděném procesu.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Rozšiřuje `ICorDebugValue` a poskytuje podporu pro `ICorDebugType`.  
  
 \ [rozhraní ICorDebugValue3 –](icordebugvalue3-interface.md)
 Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" tak, aby poskytovala podporu pro pole, která jsou větší než 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Rozšiřuje `ICorDebugBreakpoint` o poskytnutí přístupu k určitým hodnotám.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugValue` polí.  
  
 \ [rozhraní ICorDebugVariableHome](icordebugvariablehome-interface.md)
 Představuje místní proměnnou nebo argument funkce.  
  
 \ [rozhraní ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)
 Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.  
  
 \ [rozhraní ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)
 Načte informace o ladicím symbolu pro proměnnou. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)
 Poskytuje metody, které vám pomůžou při odvíjení zásobníku. **K dispozici pouze v .NET Native.**  
  
 \ [rozhraní ICorPublish –](icorpublish-interface.md)
 Slouží jako obecné rozhraní pro procesy publikování.  
  
 \ [rozhraní ICorPublishAppDomain](icorpublishappdomain-interface.md)
 Představuje a poskytuje informace o aplikační doméně.  
  
 \ [rozhraní ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md)
 Poskytuje metody, které procházejí kolekci `ICorPublishAppDomain` objektů, které aktuálně existují v rámci procesu.  
  
 \ [rozhraní ICorPublishEnum](icorpublishenum-interface.md)
 Slouží jako abstraktní základ pro enumerátory publikování.  
  
 \ [rozhraní ICorPublishProcess](icorpublishprocess-interface.md)
 Poskytuje metody, které přistupují k informacím o procesu.  
  
 \ [rozhraní ICorPublishProcessEnum –](icorpublishprocessenum-interface.md)
 Poskytuje metody, které procházejí kolekci `ICorPublishProcess` objektů.  

 \ [rozhraní ISOSDacInterface](isosdacinterface-interface.md)
 Poskytuje pomocné metody pro přístup k datům z `SOS`.

 \ [rozhraní IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
 Poskytuje metody pro dotazování na informace o definici metody.
 
 \ [rozhraní IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
 Poskytuje metody pro dotazování na informace o instanci metody.
 
 \ [rozhraní IXCLRDataModule](ixclrdatamodule-interface.md)
 Poskytuje metody pro dotazování na informace o načteném modulu.
 
 \ [rozhraní IXCLRDataProcess](ixclrdataprocess-interface.md)
 Poskytuje metody pro dotazování na informace o procesu.
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění tříd typu coclass](debugging-coclasses.md)\
 [Ladění globálních statických funkcí](debugging-global-static-functions.md)\
 \ [výčtů ladění](debugging-enumerations.md)
 \ [struktury ladění](debugging-structures.md)
