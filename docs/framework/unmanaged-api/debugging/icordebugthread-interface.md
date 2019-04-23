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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184701"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread – rozhraní
Představuje vlákno v procesu. Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Tato metoda není implementována. Nepoužívejte ho.|  
|[CreateEval – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Vytvoří objekt icordebugeval –, který funguje na tomto `ICorDebugThread`.|  
|[CreateStepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Vytvoří objekt icordebugstepper –, který umožňuje procházení aktivní rámec v tomto `ICorDebugThread`.|  
|[EnumerateChains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Získá ukazatel rozhraní k enumerátoru icordebugchainenum –, který obsahuje všechny řetězů zásobníku v tomto `ICorDebugThread`.|  
|[GetActiveChain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Získá ukazatel rozhraní k aktivní icordebugchain – v tomto `ICorDebugThread`.|  
|[GetActiveFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Získá ukazatel rozhraní k aktivní ICorDebugFrame na tomto `ICorDebugThread`.|  
|[GetAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Získá ukazatel rozhraní aplikační doménu, ve které `ICorDebugThread` právě probíhá.|  
|[GetCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje výjimku vyvolanou aktuálně ve spravovaném kódu.|  
|[GetDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Získá cordebugthreadstate – hodnota, která popisuje aktuální stav ladění této `ICorDebugThread`.|  
|[GetHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Získá aktuální popisovač pro aktivní součást této `ICorDebugThread`.|  
|[GetID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Získá identifikátor aktuálního operačního systému active součástí této `ICorDebugThread`.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Získá ukazatel rozhraní k procesu, které bude tato `ICorDebugThread` součástí.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Získá ukazatel rozhraní k sadě register přidružený k tomuto `ICorDebugThread`.|  
|[GetUserState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Získá bitová kombinace hodnot cordebuguserstate –, které popisují aktuální stav tohoto `ICorDebugThread`.|  
|[SetDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Nastaví bitová kombinace hodnot `CorDebugThreadState` hodnot, které popisují ladění stav `ICorDebugThread`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
