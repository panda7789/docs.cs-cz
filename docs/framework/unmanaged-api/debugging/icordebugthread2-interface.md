---
title: ICorDebugThread2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: fdaad46b739721ff95b712d4b6461a793ae0a480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791422"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 – rozhraní
Slouží jako logické rozšíření rozhraní ICorDebugThread.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetActiveFunctions – metoda](icordebugthread2-getactivefunctions-method.md)|Získá pole instancí COR_ACTIVE_FUNCTION, které obsahují data o aktivních funkcích v rámečcích vlákna.|  
|[GetConnectionID – metoda](icordebugthread2-getconnectionid-method.md)|Získá identifikátor připojení pro tento `ICorDebugThread2`.|  
|[GetTaskID – metoda](icordebugthread2-gettaskid-method.md)|Získá identifikátor úkolu pro tento `ICorDebugThread2`.|  
|[GetVolatileOSThreadID – metoda](icordebugthread2-getvolatileosthreadid-method.md)|Získá identifikátor vlákna operačního systému pro tento `ICorDebugThread2`.|  
|[InterceptCurrentException – metoda](icordebugthread2-interceptcurrentexception-method.md)|Umožňuje ladicímu programu zachytit aktuální výjimku ve vlákně.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
