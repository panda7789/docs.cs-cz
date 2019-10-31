---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124334"
---
# <a name="debugging-enumerations"></a>Ladění výčtů
Tato část popisuje nespravované výčty, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_PROCESS_FLAGS – výčet](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging:: OpenVirtualProcess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .  
  
 [CLRDataEnumMemoryFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Určuje, které oblasti paměti musí volání metody [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) zahrnovat.  
  
 [COR_PUB_ENUMPROCESS – výčet](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Určuje typ procesu, který se má vyčíslit.  
  
 [CorDebugBlockingReason – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Určuje důvody, proč se vlákno může v daném objektu zablokovat.  
  
 CorDebugChainReason –  
 Určuje důvod nebo důvody pro zahájení řetězu volání.  
  
 [CorDebugCodeInvokeKind – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Popisuje, jak exportovaný funkce vyvolá spravovaný kód.  
  
 [CorDebugCodeInvokePurpose – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Popisuje, proč exportovaná funkce volá spravovaný kód.  
  
 CorDebugCreateProcessFlags –  
 Poskytuje další možnosti ladění, které lze použít při volání metody [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .  
  
 [CorDebugDebugEventKind – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Určuje typ události, jejíž informace je dekódovat metodou [DecodeEvent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .  
  
 [CorDebugDecodeEventFlagsWindows – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Poskytuje další informace o událostech ladění na platformě Windows.  
  
 CorDebugExceptionCallbackType –  
 Určuje typ zpětného volání, které je provedeno z události [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) .  
  
 [CorDebugExceptionFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Poskytuje další informace o výjimce.  
  
 CorDebugExceptionUnwindCallbackType –  
 Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.  
  
 [CorDebugGCType – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Označuje, zda systém uvolňování paměti běží na pracovní stanici nebo serveru.  
  
 [CorDebugGenerationTypes – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Určuje generaci oblasti paměti na spravované haldě.  
  
 CorDebugHandleType –  
 Určuje typ popisovače.  
  
 [CorDebugIlToNativeMappingTypes – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Označuje, zda určitý rozsah nativních instrukcí odpovídá zvláštnímu regionu kódu.  
  
 CorDebugIntercept –  
 Určuje typy kódu, které mohou být na začátku.  
  
 [CorDebugInterfaceVersion – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Určuje buď verzi .NET Framework, nebo verzi .NET Framework, ve které bylo rozhraní zavedeno.  
  
 CorDebugInternalFrameType –  
 Určuje typ rámce zásobníku.  
  
 [CorDebugJITCompilerFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Obsahuje hodnoty, které mají vliv na chování spravovaného kompilátoru JIT (just-in-time).  
  
 [CorDebugJITCompilerFlagsDeprecated – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Zastaralé. Místo toho použijte `CORDEBUG_JIT_DEFAULT` člen výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .  
  
 CorDebugMappingResult –  
 Poskytuje podrobné informace o tom, jak byla získána hodnota ukazatele na instrukce (IP).  
  
 [CorDebugMDAFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Určuje stav vlákna, ve kterém je aktivován pomocník spravovaného ladění (MDA).  
  
 [CorDebugNGenPolicy – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.  
  
 [CorDebugPlatform – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .  
  
 [CorDebugRecordFormat – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Popisuje formát dat v bajtovém poli, které obsahuje informace o nativní události ladění výjimky.  
  
 CorDebugRegister –  
 Určuje Registry přidružené k dané architektuře procesoru.  
  
 [CorDebugSetContextFlag – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.  
  
 [CorDebugStateChange – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.  
  
 CorDebugStepReason –  
 Označuje výsledek jednotlivého kroku.  
  
 CorDebugThreadState –  
 Určuje stav vlákna pro ladění.  
  
 \>CorDebugUnmappedStop –  
 Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.  
  
 CorDebugUserState –  
 Určuje stav uživatele vlákna.  
  
 [CorGCReferenceType – výčet](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Určuje zdroj objektu, který má být shromážděn do paměti.  
  
 [ILCodeKind – výčet](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Poskytuje hodnoty, které určují, jestli má ladicí program přístup k místním proměnným nebo kódu přidanému v profileru ReJIT instrumentace.  
  
 [LoggingLevelEnum – výčet](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.  
  
 [LogSwitchCallReason – výčet](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Určuje operaci, která byla provedena na přepínači ladění/trasování.  
  
 [VariableLocationType – výčet](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Označuje typ nativního umístění proměnné.  
  
 [WriteableMetadataUpdateMode – výčet](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Poskytuje hodnoty, které určují, zda mají být aktualizace metadat v paměti viditelné ladicímu programu. 

 [Výčet ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Poskytuje hodnoty, které jsou používány strukturou CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
