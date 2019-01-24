---
title: ICorDebugManagedCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 516485d39f1e18a3b82886ed08cd0344c16236dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640534"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback – rozhraní
Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Break – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Upozorní ladicí program při <xref:System.Reflection.Emit.OpCodes.Break> instrukce v datovém proudu kód provádí.|  
|[Breakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Ladicí program upozorní, když zarážky.|  
|[BreakpointSetError – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Upozorní ladicí program nemohl common language runtime (CLR) přesně svázat zarážku, která byla nastavena před funkci just-in-time (JIT) zkompilována.|  
|[ControlCTrap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Upozorní ladicí program, CTRL + C je zachycena v laděném procesu.|  
|[CreateAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Upozorní ladicího programu, že se vytvořila domény aplikace.|  
|[CreateProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Ladicí program upozorní, když proces byl připojen nebo první spuštění.|  
|[CreateThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Upozorní ladicí program, vlákno se zahájilo se spuštění spravovaného kódu.|  
|[DebuggerError – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Upozorní ladicího programu, že došlo k chybě při pokusu o zpracování události z modulu CLR.|  
|[EditAndContinueRemap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Zastaralé Upozorní ladicího programu, že přemapování události odeslala do integrovaného vývojového prostředí.|  
|[EvalComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Upozorní ladicího programu, že zkušební verzi bylo dokončeno.|  
|[EvalException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Upozorní ladicího programu, že byl ukončen zkušební verzi s neošetřenou výjimkou.|  
|[Exception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Upozorní ladicího programu, že byla vyvolána výjimka ze spravovaného kódu.|  
|[ExitAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Upozorní ladicího programu, že byl ukončen domény aplikace.|  
|[ExitProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Upozorní ladicího programu, že proces byl ukončen.|  
|[ExitThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Upozorní ladicího programu, že vlákno, které se spouští spravovaný kód byl ukončen.|  
|[LoadAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Upozorní ladicího programu, že sestavení CLR byl úspěšně načten.|  
|[LoadClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Načtení třídy upozorní ladicí program.|  
|[LoadModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Upozorní ladicího programu, že modul CLR byl úspěšně načten.|  
|[LogMessage – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Upozorní ladicí program, vlákno CLR spravované volal metodu <xref:System.Diagnostics.EventLog> třídy do protokolu událostí.|  
|[LogSwitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Upozorní ladicí program, vlákno CLR spravované volal metodu <xref:System.Diagnostics.Switch> třídy k vytvoření, úpravě nebo odstranění přepínače ladění a trasování.|  
|[NameChange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Upozorní ladicího programu, že došlo ke změně názvu domény aplikace nebo vlákna.|  
|[StepComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Upozorní ladicího programu, že se dokončil krok.|  
|[UnloadAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Upozorní ladicího programu, že sestavení CLR byl uvolněn.|  
|[UnloadClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Upozorní ladicího programu, že třída uvolňován.|  
|[UnloadModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Upozorní ladicího programu, že modul CLR (DLL) byla uvolněna.|  
|[UpdateModuleSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Upozorní ladicího programu, že jste změnili symbolů pro modul CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny zpětná volání jsou serializován, názvem ve stejném vlákně a volá se v procesu synchronizované stavové.  
  
 Každá implementace zpětného volání musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pokračovat provádění. Pokud `ICorDebugController::Continue` není volána před zpětného volání vrátí, zůstane zastaven proces a žádná další zpětná volání události dojde až do `ICorDebugController::Continue` je volána.  
  
 Ladicí program musí implementovat [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) pokud ji je ladění aplikace rozhraní .NET Framework verze 2.0. Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` je předán jako objekt zpětného volání k [icordebug::setmanagedhandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
