---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b81e7c2ffabdee78af34d00c48fb29c7525dea08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-enumerations"></a>Ladění výčtů
Tato část popisuje nespravovaná vyčíslení, která používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_PROCESS_FLAGS – výčet](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda.  
  
 [CLRDataEnumMemoryFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Určuje, které oblasti paměti volání [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda by měla obsahovat.  
  
 [COR_PUB_ENUMPROCESS – výčet](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Určuje typ procesu výčet.  
  
 [CorDebugBlockingReason – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Určuje z důvodů, proč může zablokování vlákna na daný objekt.  
  
 CorDebugChainReason  
 Označuje důvod nebo důvody pro zahájení řetěz volání.  
  
 [CorDebugCodeInvokeKind – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Popisuje, jak exportované funkce vyvolá spravovaného kódu.  
  
 [CorDebugCodeInvokePurpose – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Popisuje, proč exportované funkce volá spravovaného kódu.  
  
 CorDebugCreateProcessFlags  
 Poskytuje další možnosti ladění, které mohou být používány volání [icordebug::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metoda.  
  
 [CorDebugDebugEventKind – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Určuje typ události, jejichž informace dekóduje ji [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda.  
  
 [CorDebugDecodeEventFlagsWindows – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Poskytuje další informace o ladění událostí na platformě Windows.  
  
 CorDebugExceptionCallbackType  
 Určuje typ zpětné volání, které se provádí z [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) událostí.  
  
 [CorDebugExceptionFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Poskytuje další informace o výjimce.  
  
 CorDebugExceptionUnwindCallbackType  
 Označuje událost, která se během fáze unwind signalizace podle zpětné volání.  
  
 [CorDebugGCType – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Určuje, zda má systém uvolňování běží na pracovní stanici nebo na serveru.  
  
 [CorDebugGenerationTypes – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Spravovaná halda určuje generování oblasti paměti.  
  
 CorDebugHandleType  
 Určuje typ popisovače.  
  
 [CorDebugIlToNativeMappingTypes – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Určuje, jestli konkrétní rozsah nativní pokyny odpovídá speciální kód oblasti.  
  
 CorDebugIntercept  
 Určuje typy kód, který může mít stupně do.  
  
 [CorDebugInterfaceVersion – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Určuje verzi rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve kterém byla zavedena rozhraní.  
  
 CorDebugInternalFrameType  
 Určuje typ rámce zásobníku.  
  
 [CorDebugJITCompilerFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Obsahuje hodnoty, které ovlivňují chování objektu spravovaného kompilátoru za běhu (JIT).  
  
 [CorDebugJITCompilerFlagsDeprecated – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Zastaralé. Použití `CORDEBUG_JIT_DEFAULT` členem [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) – výčet místo.  
  
 CorDebugMappingResult  
 Poskytuje podrobnosti o tom, jak byla získána hodnota ukazatele instrukce (IP).  
  
 [CorDebugMDAFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Určuje stav vláken, na kterém je aktivována, Pomocník spravovaného ladění (MDA).  
  
 [CorDebugNGenPolicy – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Obsahuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměť nativních bitových kopií.  
  
 [CorDebugPlatform – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Poskytuje cílové platformy hodnoty, které jsou používány [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metoda.  
  
 [CorDebugRecordFormat – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Popisuje formát dat v bajtové pole obsahující informace o události ladění nativního výjimka.  
  
 CorDebugRegister  
 Určuje registry spojené s danou procesoru architektura.  
  
 [CorDebugSetContextFlag – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Určuje, zda kontext je z aktivní (nebo listu) s rámečkem v zásobníku nebo je poškozený podle unwinding z jiné rámce.  
  
 [CorDebugStateChange – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Popisuje množství uložené v mezipaměti dat, která musí být odstraněn podle změn do procesu.  
  
 CorDebugStepReason  
 Určuje výsledek jednotlivé kroky.  
  
 CorDebugThreadState  
 Určuje stav vláken pro ladění.  
  
 \>CorDebugUnmappedStop  
 Určuje typ nenamapovaný kód, který můžete aktivovat zastavení provádění kódu pomocí krokovače.  
  
 CorDebugUserState  
 Určuje stav uživatele vlákna.  
  
 [CorGCReferenceType – výčet](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Určuje zdroj objekt tak, aby se uvolňování paměti.  
  
 [ILCodeKind – výčet](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Obsahuje hodnoty, které určují, jestli je přístup k místní proměnné nebo kódu přidaném v ReJIT instrumentace profileru ladicího programu.  
  
 [LoggingLevelEnum – výčet](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Určuje úroveň závažnosti popisný zprávu, která se zapíšou do protokolu událostí, když spravované vlákno protokoluje nějakou událost.  
  
 [LogSwitchCallReason – výčet](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Určuje operaci, která byla provedena na přepínači ladění nebo trasování.  
  
 [VariableLocationType – výčet](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Označuje typ nativní umístění proměnné.  
  
 [WriteableMetadataUpdateMode – výčet](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Obsahuje hodnoty, které určují, zda jsou viditelné pro ladicí program aktualizace v paměti pro metadata.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
