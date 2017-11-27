---
title: ICorDebugThread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b5c8f0720402cce56c69394c6fbe2fb70a6177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread-interface1"></a>ICorDebugThread Interface1
Představuje vlákno v procesu. Životnost `ICorDebugThread` instance je stejný jako životnost vlákno reprezentuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clearcurrentexception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Tato metoda není implementována. Nepoužívejte ho.|  
|[Createeval – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Vytvoří objekt ICorDebugEval, který funguje na tomto `ICorDebugThread`.|  
|[Createstepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Vytvoří objekt ICorDebugStepper, který umožňuje procházení active rámečku v tomto `ICorDebugThread`.|  
|[Enumeratechains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Získá ukazatele rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread`.|  
|[Getactivechain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Získá ukazatele rozhraní k active ICorDebugChain na tomto `ICorDebugThread`.|  
|[Getactiveframe – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Získá ukazatele rozhraní k active ICorDebugFrame na tomto `ICorDebugThread`.|  
|[Getappdomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Získá ukazatele rozhraní do domény aplikace, v němž je tato `ICorDebugThread` právě probíhá.|  
|[Getcurrentexception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Získá ukazatele rozhraní ICorDebugValue objektu, která představuje výjimku aktuálně hlášeny ve spravovaném kódu.|  
|[Getdebugstate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Získá hodnotu CorDebugThreadState, která popisuje aktuální stav ladění tohoto `ICorDebugThread`.|  
|[Gethandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Získá aktuální popisovač pro aktivní součást tohoto `ICorDebugThread`.|  
|[Getid – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Získá identifikátor operační systém aktuální aktivní součást tohoto `ICorDebugThread`.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Získá ukazatele rozhraní pro běžné vlákno language runtime (CLR).|  
|[Getprocess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Získá ukazatele rozhraní, které tento proces `ICorDebugThread` součástí.|  
|[Getregisterset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Získá ukazatele rozhraní do sady registrace, který je přidružený k tomuto `ICorDebugThread`.|  
|[Getuserstate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Získá bitovou kombinaci hodnot CorDebugUserState, které popisují aktuální stav tohoto `ICorDebugThread`.|  
|[Setdebugstate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Nastaví bitovou kombinaci `CorDebugThreadState` hodnoty, které popisují ladění stav tohoto `ICorDebugThread`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
