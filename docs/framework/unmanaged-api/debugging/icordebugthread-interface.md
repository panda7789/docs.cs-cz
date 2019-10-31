---
title: ICorDebugThread – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133501"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread – rozhraní
Představuje vlákno v procesu. Doba životnosti `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Tato metoda není implementována. Nepoužívejte ho.|  
|[CreateEval – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Vytvoří objekt ICorDebugEval, který pracuje na tomto `ICorDebugThread`.|  
|[CreateStepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Vytvoří objekt ICorDebugStepper, který umožňuje krokování skrze aktivní rámec tohoto `ICorDebugThread`.|  
|[EnumerateChains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Získá ukazatel rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread`.|  
|[GetActiveChain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Získá ukazatel rozhraní na aktivní ICorDebugChain na tomto `ICorDebugThread`.|  
|[GetActiveFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Získá ukazatel rozhraní na aktivní ICorDebugFrame na tomto `ICorDebugThread`.|  
|[GetAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Získá ukazatel rozhraní na doménu aplikace, ve které je právě prováděna tato `ICorDebugThread`.|  
|[GetCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje výjimku aktuálně vyvolanou spravovaným kódem.|  
|[GetDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Získá hodnotu CorDebugThreadState –, která popisuje aktuální stav ladění tohoto `ICorDebugThread`.|  
|[GetHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Získá aktuální popisovač pro aktivní část tohoto `ICorDebugThread`.|  
|[GetID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Načte aktuální identifikátor operačního systému aktivní části tohoto `ICorDebugThread`.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Načte ukazatel rozhraní do vlákna modulu CLR (Common Language Runtime).|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Získá ukazatel rozhraní na proces, na který `ICorDebugThread` tvoří součást.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Získá ukazatel rozhraní na sadu registrů přidruženou k tomuto `ICorDebugThread`.|  
|[GetUserState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Získá bitovou kombinaci hodnot CorDebugUserState –, které popisují aktuální stav tohoto `ICorDebugThread`.|  
|[SetDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Nastaví bitovou kombinaci hodnot `CorDebugThreadState`, které popisují stav ladění tohoto `ICorDebugThread`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
