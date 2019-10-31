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
ms.openlocfilehash: 96dedcd27e87c5afc504e7840100eb121410675e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130758"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback – rozhraní
Poskytuje metody pro zpětná volání procesu ladicího programu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Break – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Upozorní ladicí program, když se spustí instrukce <xref:System.Reflection.Emit.OpCodes.Break> v datovém proudu kódu.|  
|[Breakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Upozorní ladicí program, když dojde k zarážce.|  
|[BreakpointSetError – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Oznamuje ladicímu programu, že modul CLR (Common Language Runtime) nedokázal přesně navazovat zarážku, která byla nastavena předtím, než byla funkce kompilována za běhu (just-in-time).|  
|[ControlCTrap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Oznamuje ladicímu programu, že kombinace kláves CTRL + C je zachycena v laděném procesu.|  
|[CreateAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Oznamuje ladicímu programu, že byla vytvořena doména aplikace.|  
|[CreateProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Upozorní ladicí program, když byl proces poprvé připojen nebo spuštěn.|  
|[CreateThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Oznamuje ladicímu programu, že vlákno zahájilo provádění spravovaného kódu.|  
|[DebuggerError – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Oznamuje ladicímu programu, že došlo k chybě při pokusu o zpracování události z CLR.|  
|[EditAndContinueRemap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Zastaralé Oznamuje ladicímu programu, že byla do integrovaného vývojového prostředí odeslána událost přemapování.|  
|[EvalComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Oznamuje ladicímu programu, že bylo dokončeno vyhodnocení.|  
|[EvalException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Oznamuje ladicímu programu, že vyhodnocení skončilo neošetřenou výjimkou.|  
|[Exception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Oznamuje ladicímu programu, že byla vyvolána výjimka ze spravovaného kódu.|  
|[ExitAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Oznamuje ladicímu programu, že doména aplikace byla ukončena.|  
|[ExitProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Oznamuje ladicímu programu, že došlo k ukončení procesu.|  
|[ExitThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Oznamuje ladicímu programu, že bylo ukončeno vlákno, které spustilo spravovaný kód.|  
|[LoadAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Oznamuje ladicímu programu, že bylo úspěšně načteno sestavení CLR.|  
|[LoadClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Oznamuje ladicímu programu, že byla načtena třída.|  
|[LoadModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Oznamuje ladicímu programu, že modul CLR byl úspěšně načten.|  
|[LogMessage – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Oznamuje ladicímu programu, že spravované vlákno CLR volalo metodu ve třídě <xref:System.Diagnostics.EventLog> k zaznamenání události.|  
|[LogSwitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Oznamuje ladicímu programu, že spravované vlákno CLR volalo metodu ve třídě <xref:System.Diagnostics.Switch> k vytvoření, úpravě nebo odstranění přepínače ladění/trasování.|  
|[NameChange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Oznamuje ladicímu programu, že došlo ke změně názvu domény aplikace nebo vlákna.|  
|[StepComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Oznamuje ladicímu programu, že byl krok dokončen.|  
|[UnloadAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Oznamuje ladicímu programu, že bylo uvolněno sestavení CLR.|  
|[UnloadClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Oznamuje ladicímu programu, že je třída uvolňována.|  
|[UnloadModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Oznamuje ladicímu programu, že byl uvolněn modul CLR (DLL).|  
|[UpdateModuleSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Oznamuje ladicímu programu, že se změnily symboly modulu CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Všechna zpětná volání jsou serializována, volána ve stejném vlákně a volána s procesem v synchronizovaném stavu.  
  
 Každé implementaci zpětného volání musí volat metodu [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby bylo možné pokračovat v provádění. Pokud `ICorDebugController::Continue` není volána před vrácením zpětného volání, proces zůstane zastaven a žádné další zpětné volání události nebude provedeno, dokud `ICorDebugController::Continue` není volána.  
  
 Ladicí program musí implementovat [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) , pokud ladí aplikace .NET Framework aplikací verze 2,0. Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` je předána jako objekt zpětného volání do [ICorDebug:: SetManagedHandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
