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
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415946"
---
# <a name="debugging-enumerations"></a>Ladění výčtů
Tato část popisuje nespravované výčty, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_PROCESS_FLAGS – výčet](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.  
  
 [CLRDataEnumMemoryFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Označuje volání, které oblasti paměti [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda by měla obsahovat.  
  
 [COR_PUB_ENUMPROCESS – výčet](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Určuje typ procesu vytvoření výčtu.  
  
 [CorDebugBlockingReason – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Určuje důvody, proč může zablokování vlákna na daný objekt.  
  
 CorDebugChainReason  
 Označuje důvod nebo důvodů, proč inicializační řetězec volání.  
  
 [CorDebugCodeInvokeKind – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Popisuje, jak exportované funkce volá spravovaný kód.  
  
 [CorDebugCodeInvokePurpose – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Popisuje, proč exportované funkce volá spravovaný kód.  
  
 CorDebugCreateProcessFlags  
 Poskytuje další možnosti ladění, které lze použít ve volání [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.  
  
 [CorDebugDebugEventKind – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Určuje typ události, jejichž informace je dekódováno pomocí [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.  
  
 [CorDebugDecodeEventFlagsWindows – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Poskytuje další informace o ladění událostí na platformě Windows.  
  
 CorDebugExceptionCallbackType  
 Určuje typ zpětné volání, které se provádí ze [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) událostí.  
  
 [CorDebugExceptionFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Poskytuje další informace o výjimce.  
  
 CorDebugExceptionUnwindCallbackType  
 Určuje události, ke které je právě signalizována zpětného volání ve fázi unwind.  
  
 [CorDebugGCType – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Určuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.  
  
 [CorDebugGenerationTypes – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Určuje generování oblast paměti na spravované haldě.  
  
 Cordebughandletype –  
 Určuje typ popisovače.  
  
 [CorDebugIlToNativeMappingTypes – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Označuje, zda určitý rozsah nativní pokyny odpovídá speciální kód oblasti.  
  
 CorDebugIntercept  
 Určuje typy kódu, který může být vkročili.  
  
 [CorDebugInterfaceVersion – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Určuje verzi rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve kterém byl zaveden rozhraní.  
  
 CorDebugInternalFrameType  
 Určuje typ rámce zásobníku.  
  
 [CorDebugJITCompilerFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Obsahuje hodnoty, které ovlivňují chování spravované kompilátor just-in-time (JIT).  
  
 [CorDebugJITCompilerFlagsDeprecated – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Zastaralé. Použití `CORDEBUG_JIT_DEFAULT` člena [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet místo.  
  
 CorDebugMappingResult  
 Poskytuje podrobnosti o způsobu získání hodnoty ukazatel instrukce (IP).  
  
 [CorDebugMDAFlags – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Určuje stav vláken, ve kterém se spustí Pomocník spravovaného ladění (MDA).  
  
 [CorDebugNGenPolicy – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Poskytuje hodnotu, která určuje, zda ladicí program načítá nativní bitové kopie (NGen) z mezipaměti nativních bitových kopií.  
  
 [CorDebugPlatform – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Poskytuje cílové platformy hodnoty, které jsou používány [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.  
  
 [CorDebugRecordFormat – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Popisuje formát dat v bajtové pole, která obsahuje informace o události ladění nativní výjimka.  
  
 Cordebugregister –  
 Určuje registrů spojené s danou procesor architektury.  
  
 [CorDebugSetContextFlag – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Určuje, zda je kontext z aktivního (nebo listu) rámce v zásobníku nebo byl vypočítán pomocí návrat zpět z jiného snímku.  
  
 [CorDebugStateChange – výčet](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Popisuje množství dat uložených v mezipaměti, který musí být odstraněn podle změn do procesu.  
  
 CorDebugStepReason  
 Určuje výsledek jednotlivé kroky.  
  
 Cordebugthreadstate –  
 Určuje stav vlákna pro ladění.  
  
 \>Cordebugunmappedstop –  
 Určuje typ nenamapované kód, který můžete aktivovat zastavení provádění kódu pomocí krokovače.  
  
 CorDebugUserState  
 Určuje stav uživatele vlákna.  
  
 [CorGCReferenceType – výčet](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Identifikuje zdrojový objekt bude uvolněna.  
  
 [ILCodeKind – výčet](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Obsahuje hodnoty, které určují, jestli je přístup k lokálním proměnným nebo kód přidaný v profileru instrumentace ReJIT ladicí program.  
  
 [LoggingLevelEnum – výčet](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Určuje úroveň závažnosti popisnou zprávou, která jsou zapsána do protokolu událostí při spravovaným vláknem se zaprotokoluje událost.  
  
 [LogSwitchCallReason – výčet](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Určuje operaci, která byla provedena na přepínači ladění a trasování.  
  
 [VariableLocationType – výčet](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Určuje umístění nativní typ proměnné.  
  
 [WriteableMetadataUpdateMode – výčet](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Obsahuje hodnoty, které určují, jestli jsou viditelné pro ladicí program v paměti aktualizace metadat. 

 [Výčet ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.

## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
