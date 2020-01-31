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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791479"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread – rozhraní
Představuje vlákno v procesu. Doba životnosti `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](icordebugthread-clearcurrentexception-method.md)|Tato metoda není implementována. Nepoužívejte ho.|  
|[CreateEval – metoda](icordebugthread-createeval-method.md)|Vytvoří objekt ICorDebugEval, který pracuje na tomto `ICorDebugThread`.|  
|[CreateStepper – metoda](icordebugthread-createstepper-method.md)|Vytvoří objekt ICorDebugStepper, který umožňuje krokování skrze aktivní rámec tohoto `ICorDebugThread`.|  
|[EnumerateChains – metoda](icordebugthread-enumeratechains-method.md)|Získá ukazatel rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread`.|  
|[GetActiveChain – metoda](icordebugthread-getactivechain-method.md)|Získá ukazatel rozhraní na aktivní ICorDebugChain na tomto `ICorDebugThread`.|  
|[GetActiveFrame – metoda](icordebugthread-getactiveframe-method.md)|Získá ukazatel rozhraní na aktivní ICorDebugFrame na tomto `ICorDebugThread`.|  
|[GetAppDomain – metoda](icordebugthread-getappdomain-method.md)|Získá ukazatel rozhraní na doménu aplikace, ve které je právě prováděna tato `ICorDebugThread`.|  
|[GetCurrentException – metoda](icordebugthread-getcurrentexception-method.md)|Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje výjimku aktuálně vyvolanou spravovaným kódem.|  
|[GetDebugState – metoda](icordebugthread-getdebugstate-method.md)|Získá hodnotu CorDebugThreadState –, která popisuje aktuální stav ladění tohoto `ICorDebugThread`.|  
|[GetHandle – metoda](icordebugthread-gethandle-method.md)|Získá aktuální popisovač pro aktivní část tohoto `ICorDebugThread`.|  
|[GetID – metoda](icordebugthread-getid-method.md)|Načte aktuální identifikátor operačního systému aktivní části tohoto `ICorDebugThread`.|  
|[GetObject – metoda](icordebugthread-getobject-method.md)|Načte ukazatel rozhraní do vlákna modulu CLR (Common Language Runtime).|  
|[GetProcess – metoda](icordebugthread-getprocess-method.md)|Získá ukazatel rozhraní na proces, na který `ICorDebugThread` tvoří součást.|  
|[GetRegisterSet – metoda](icordebugthread-getregisterset-method.md)|Získá ukazatel rozhraní na sadu registrů přidruženou k tomuto `ICorDebugThread`.|  
|[GetUserState – metoda](icordebugthread-getuserstate-method.md)|Získá bitovou kombinaci hodnot CorDebugUserState –, které popisují aktuální stav tohoto `ICorDebugThread`.|  
|[SetDebugState – metoda](icordebugthread-setdebugstate-method.md)|Nastaví bitovou kombinaci hodnot `CorDebugThreadState`, které popisují stav ladění tohoto `ICorDebugThread`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
