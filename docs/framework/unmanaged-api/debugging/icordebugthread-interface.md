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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379823"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread – rozhraní
Představuje vlákno v procesu. Doba života `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](icordebugthread-clearcurrentexception-method.md)|Tato metoda není implementována. Nepoužívejte ho.|  
|[CreateEval – metoda](icordebugthread-createeval-method.md)|Vytvoří objekt ICorDebugEval, který na tomto počítači pracuje `ICorDebugThread` .|  
|[CreateStepper – metoda](icordebugthread-createstepper-method.md)|Vytvoří objekt ICorDebugStepper, který umožňuje krokování přes aktivní rámec v tomto `ICorDebugThread` .|  
|[EnumerateChains – metoda](icordebugthread-enumeratechains-method.md)|Získá ukazatel rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread` .|  
|[GetActiveChain – metoda](icordebugthread-getactivechain-method.md)|Získá ukazatel rozhraní na aktivní ICorDebugChain `ICorDebugThread` .|  
|[GetActiveFrame – metoda](icordebugthread-getactiveframe-method.md)|Získá ukazatel rozhraní na aktivní ICorDebugFrame `ICorDebugThread` .|  
|[GetAppDomain – metoda](icordebugthread-getappdomain-method.md)|Získá ukazatel rozhraní na doménu aplikace, ve které `ICorDebugThread` je aktuálně prováděna.|  
|[GetCurrentException – metoda](icordebugthread-getcurrentexception-method.md)|Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje výjimku aktuálně vyvolanou spravovaným kódem.|  
|[GetDebugState – metoda](icordebugthread-getdebugstate-method.md)|Získá hodnotu CorDebugThreadState –, která popisuje aktuální stav ladění tohoto `ICorDebugThread` .|  
|[GetHandle – metoda](icordebugthread-gethandle-method.md)|Získá aktuální popisovač pro aktivní část tohoto `ICorDebugThread` .|  
|[GetID – metoda](icordebugthread-getid-method.md)|Získá aktuální identifikátor operačního systému aktivní části tohoto `ICorDebugThread` .|  
|[GetObject – metoda](icordebugthread-getobject-method.md)|Načte ukazatel rozhraní do vlákna modulu CLR (Common Language Runtime).|  
|[GetProcess – metoda](icordebugthread-getprocess-method.md)|Získá ukazatel rozhraní na proces, který `ICorDebugThread` tvoří součást.|  
|[GetRegisterSet – metoda](icordebugthread-getregisterset-method.md)|Získá ukazatel rozhraní na sadu registrů přidruženou k tomuto `ICorDebugThread` .|  
|[GetUserState – metoda](icordebugthread-getuserstate-method.md)|Získá bitovou kombinaci hodnot CorDebugUserState –, které popisují aktuální stav `ICorDebugThread` .|  
|[SetDebugState – metoda](icordebugthread-setdebugstate-method.md)|Nastaví bitovou kombinaci `CorDebugThreadState` hodnot, které popisují stav ladění this `ICorDebugThread` .|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
