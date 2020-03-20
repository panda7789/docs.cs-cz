---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: c37b6ff42b428184d301d63b6dbbd9d80a72bf3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179144"
---
# <a name="debugging-enumerations"></a>Ladění výčtů
Tato část popisuje nespravované výčty, které používá ladění rozhraní API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_PROCESS_FLAGS – výčet](clr-debugging-process-flags-enumeration.md)  
 Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging::OpenVirtualProcess.](iclrdebugging-openvirtualprocess-method.md)  
  
 [CLRDataEnumMemoryFlags – výčet](clrdataenummemoryflags-enumeration.md)  
 Označuje, které oblasti paměti by mělo být zahrnuto do oblastí volání metody [ICLRDataEnumMemoryRegions::EnumMemoryRegions.](iclrdataenummemoryregions-enummemoryregions-method.md)  
  
 [COR_PUB_ENUMPROCESS – výčet](cor-pub-enumprocess-enumeration.md)  
 Určuje typ procesu, který má být uveden ve výčtu.  
  
 [CorDebugBlockingReason – výčet](cordebugblockingreason-enumeration.md)  
 Určuje důvody, proč může být vlákno blokováno na daném objektu.  
  
 CorDebugChainReason  
 Označuje důvod nebo důvody pro zahájení řetězce volání.  
  
 [Výčet CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md)  
 Popisuje, jak exportovaná funkce vyvolá spravovaný kód.  
  
 [CorDebugCodeInvokePurpose – výčet](cordebugcodeinvokepurpose-enumeration.md)  
 Popisuje, proč exportovaná funkce volá spravovaný kód.  
  
 CorDebugCreateProcessFlags  
 Poskytuje další možnosti ladění, které lze použít při volání metody [ICorDebug::CreateProcess.](icordebug-createprocess-method.md)  
  
 [CorDebugDebugEventKind – výčet](cordebugdebugeventkind-enumeration.md)  
 Označuje typ události, jejíž informace jsou dekódovány metodou [DecodeEvent.](icordebugprocess6-decodeevent-method.md)  
  
 [Výčet CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md)  
 Obsahuje další informace o ladicích událostech na platformě Windows.  
  
 Typ příkazu CorDebugExceptionCallbackType  
 Označuje typ zpětného volání, který je vyroben z [Události ICorDebugManagedCallback2::Exception.](icordebugmanagedcallback2-exception-method.md)  
  
 [CorDebugExceptionFlags – výčet](cordebugexceptionflags-enumeration.md)  
 Obsahuje další informace o výjimce.  
  
 CorDebugExceptionUnwindbackType  
 Označuje událost, která je signalizována zpětného volání během fáze unwind.  
  
 [CorDebugGCType – výčet](cordebuggctype-enumeration.md)  
 Označuje, zda je systém uvolňování paměti spuštěn na pracovní stanici nebo na serveru.  
  
 [CorDebugGenerationTypes – výčet](cordebuggenerationtypes-enumeration.md)  
 Určuje generování oblasti paměti na spravované haldě.  
  
 CorDebugHandleType  
 Označuje typ popisovače.  
  
 [CorDebugIlToNativeMappingTypes – výčet](cordebugiltonativemappingtypes-enumeration.md)  
 Označuje, zda určitý rozsah nativní pokyny odpovídá zvláštní kód oblasti.  
  
 CorDebugIntercept  
 Označuje typy kódu, do kterého lze zasílat.  
  
 [CorDebugInterfaceVersion – výčet](cordebuginterfaceversion-enumeration.md)  
 Určuje verzi rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve které bylo zavedeno rozhraní.  
  
 CorDebugInternalFrameType  
 Identifikuje typ rámce zásobníku.  
  
 [CorDebugJITCompilerFlags – výčet](cordebugjitcompilerflags-enumeration.md)  
 Obsahuje hodnoty, které ovlivňují chování spravovaného kompilátoru just-in-time (JIT).  
  
 [CorDebugJITCompilerFlagsDeprecated – výčet](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Zastaralé. Použijte `CORDEBUG_JIT_DEFAULT` člen [corDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) výčtu místo.  
  
 Výsledek mapování cordebug  
 Obsahuje podrobnosti o tom, jak byla získána hodnota ukazatele instrukce (IP).  
  
 [CorDebugMDAFlags – výčet](cordebugmdaflags-enumeration.md)  
 Určuje stav vlákna, na kterém je aktivován aditovaný pomocník pro ladění (MDA).  
  
 [CorDebugNGenPolicy – výčet](cordebugngenpolicy-enumeration.md)  
 Poskytuje hodnotu, která určuje, zda ladicí program načte nativní (NGen) obrazy z nativní mezipaměti bitové kopie.  
  
 [Výčet CorDebugPlatform](cordebugplatform-enumeration.md)  
 Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget::GetPlatform.](icordebugdatatarget-getplatform-method.md)  
  
 [Výčet CorDebugRecordFormat](cordebugrecordformat-enumeration.md)  
 Popisuje formát dat v bajtovém poli, které obsahuje informace o události ladění nativní výjimky.  
  
 CorDebugRegister  
 Určuje registry přidružené k dané architektuře procesoru.  
  
 [CorDebugSetContextFlag – výčet](cordebugsetcontextflag-enumeration.md)  
 Označuje, zda je kontext z aktivního (nebo listového) rámce v zásobníku nebo byl vypočítán odvíjením z jiného rámce.  
  
 [CorDebugStateChange – výčet](cordebugstatechange-enumeration.md)  
 Popisuje množství dat uložených v mezipaměti, která musí být zahozena na základě změn procesu.  
  
 CorDebugStepReason  
 Označuje výsledek jednotlivého kroku.  
  
 CorDebugThreadState  
 Určuje stav vlákna pro ladění.  
  
 \>CorDebugUnmappedStop  
 Určuje typ nenamapovaného kódu, který může spustit zastavení provádění kódu krokovačem.  
  
 Stav uživatele cordebug  
 Označuje stav uživatele vlákna.  
  
 [CorGCReferenceType – výčet](corgcreferencetype-enumeration.md)  
 Identifikuje zdroj objektu, který má být uvolněn.  
  
 [ILCodeKind – výčet](ilcodekind-enumeration.md)  
 Poskytuje hodnoty, které určují, zda ladicí program je schopen přistupovat k místním proměnným nebo kódu přidanému v instrumentaci ReJIT profileru.  
  
 [LoggingLevelEnum – výčet](logginglevelenum-enumeration.md)  
 Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.  
  
 [LogSwitchCallReason – výčet](logswitchcallreason-enumeration.md)  
 Označuje operaci, která byla provedena na přepínači ladění/trasování.  
  
 [VariableLocationType – výčet](variablelocationtype-enumeration.md)  
 Označuje nativní typ umístění proměnné.  
  
 [Výčet WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md)  
 Poskytuje hodnoty, které určují, zda jsou aktualizace metadat v paměti viditelné pro ladicí program.

 [Výčet clrDataSourceType](clrdatasourcetype-enumeration.md) Obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.

## <a name="related-sections"></a>Související oddíly  
 [Ladění tříd typu coclass](debugging-coclasses.md)  
  
 [Debugging – rozhraní](debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](debugging-global-static-functions.md)  
  
 [Struktury pro ladění](debugging-structures.md)
