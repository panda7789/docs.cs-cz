---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789158"
---
# <a name="debugging-enumerations"></a>Ladění výčtů
Tato část popisuje nespravované výčty, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_PROCESS_FLAGS – výčet](clr-debugging-process-flags-enumeration.md)  
 Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) .  
  
 [CLRDataEnumMemoryFlags – výčet](clrdataenummemoryflags-enumeration.md)  
 Určuje, které oblasti paměti musí volání metody [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) zahrnovat.  
  
 [COR_PUB_ENUMPROCESS – výčet](cor-pub-enumprocess-enumeration.md)  
 Určuje typ procesu, který se má vyčíslit.  
  
 [CorDebugBlockingReason – výčet](cordebugblockingreason-enumeration.md)  
 Určuje důvody, proč se vlákno může v daném objektu zablokovat.  
  
 CorDebugChainReason –  
 Určuje důvod nebo důvody pro zahájení řetězu volání.  
  
 [CorDebugCodeInvokeKind – výčet](cordebugcodeinvokekind-enumeration.md)  
 Popisuje, jak exportovaný funkce vyvolá spravovaný kód.  
  
 [CorDebugCodeInvokePurpose – výčet](cordebugcodeinvokepurpose-enumeration.md)  
 Popisuje, proč exportovaná funkce volá spravovaný kód.  
  
 CorDebugCreateProcessFlags  
 Poskytuje další možnosti ladění, které lze použít při volání metody [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .  
  
 [CorDebugDebugEventKind – výčet](cordebugdebugeventkind-enumeration.md)  
 Určuje typ události, jejíž informace je dekódovat metodou [DecodeEvent –](icordebugprocess6-decodeevent-method.md) .  
  
 [CorDebugDecodeEventFlagsWindows – výčet](cordebugdecodeeventflagswindows-enumeration.md)  
 Poskytuje další informace o událostech ladění na platformě Windows.  
  
 CorDebugExceptionCallbackType  
 Určuje typ zpětného volání, které je provedeno z události [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .  
  
 [CorDebugExceptionFlags – výčet](cordebugexceptionflags-enumeration.md)  
 Poskytuje další informace o výjimce.  
  
 CorDebugExceptionUnwindCallbackType  
 Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.  
  
 [CorDebugGCType – výčet](cordebuggctype-enumeration.md)  
 Označuje, zda systém uvolňování paměti běží na pracovní stanici nebo serveru.  
  
 [CorDebugGenerationTypes – výčet](cordebuggenerationtypes-enumeration.md)  
 Určuje generaci oblasti paměti na spravované haldě.  
  
 CorDebugHandleType –  
 Určuje typ popisovače.  
  
 [CorDebugIlToNativeMappingTypes – výčet](cordebugiltonativemappingtypes-enumeration.md)  
 Označuje, zda určitý rozsah nativních instrukcí odpovídá zvláštnímu regionu kódu.  
  
 CorDebugIntercept –  
 Určuje typy kódu, které mohou být na začátku.  
  
 [CorDebugInterfaceVersion – výčet](cordebuginterfaceversion-enumeration.md)  
 Určuje buď verzi .NET Framework, nebo verzi .NET Framework, ve které bylo rozhraní zavedeno.  
  
 CorDebugInternalFrameType  
 Určuje typ rámce zásobníku.  
  
 [CorDebugJITCompilerFlags – výčet](cordebugjitcompilerflags-enumeration.md)  
 Obsahuje hodnoty, které mají vliv na chování spravovaného kompilátoru JIT (just-in-time).  
  
 [CorDebugJITCompilerFlagsDeprecated – výčet](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Zastaralé. Místo toho použijte `CORDEBUG_JIT_DEFAULT` člen výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) .  
  
 CorDebugMappingResult  
 Poskytuje podrobné informace o tom, jak byla získána hodnota ukazatele na instrukce (IP).  
  
 [CorDebugMDAFlags – výčet](cordebugmdaflags-enumeration.md)  
 Určuje stav vlákna, ve kterém je aktivován pomocník spravovaného ladění (MDA).  
  
 [CorDebugNGenPolicy – výčet](cordebugngenpolicy-enumeration.md)  
 Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.  
  
 [CorDebugPlatform – výčet](cordebugplatform-enumeration.md)  
 Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .  
  
 [CorDebugRecordFormat – výčet](cordebugrecordformat-enumeration.md)  
 Popisuje formát dat v bajtovém poli, které obsahuje informace o nativní události ladění výjimky.  
  
 CorDebugRegister –  
 Určuje Registry přidružené k dané architektuře procesoru.  
  
 [CorDebugSetContextFlag – výčet](cordebugsetcontextflag-enumeration.md)  
 Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.  
  
 [CorDebugStateChange – výčet](cordebugstatechange-enumeration.md)  
 Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.  
  
 CorDebugStepReason  
 Označuje výsledek jednotlivého kroku.  
  
 CorDebugThreadState –  
 Určuje stav vlákna pro ladění.  
  
 \>CorDebugUnmappedStop –  
 Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.  
  
 CorDebugUserState –  
 Určuje stav uživatele vlákna.  
  
 [CorGCReferenceType – výčet](corgcreferencetype-enumeration.md)  
 Určuje zdroj objektu, který má být shromážděn do paměti.  
  
 [ILCodeKind – výčet](ilcodekind-enumeration.md)  
 Poskytuje hodnoty, které určují, jestli má ladicí program přístup k místním proměnným nebo kódu přidanému v profileru ReJIT instrumentace.  
  
 [LoggingLevelEnum – výčet](logginglevelenum-enumeration.md)  
 Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.  
  
 [LogSwitchCallReason – výčet](logswitchcallreason-enumeration.md)  
 Určuje operaci, která byla provedena na přepínači ladění/trasování.  
  
 [VariableLocationType – výčet](variablelocationtype-enumeration.md)  
 Označuje typ nativního umístění proměnné.  
  
 [WriteableMetadataUpdateMode – výčet](writeablemetadataupdatemode-enumeration.md)  
 Poskytuje hodnoty, které určují, zda mají být aktualizace metadat v paměti viditelné ladicímu programu. 

 [Výčet ClrDataSourceType](clrdatasourcetype-enumeration.md) Poskytuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP strukturou.

## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](debugging-coclasses.md)  
  
 [Rozhraní pro ladění](debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](debugging-global-static-functions.md)  
  
 [Struktury pro ladění](debugging-structures.md)
