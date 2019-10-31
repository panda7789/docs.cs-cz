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
ms.openlocfilehash: 49d0015e9d8390a47aae7ce497dd431dfe743c36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138670"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 – rozhraní
Slouží jako logické rozšíření rozhraní ICorDebugThread.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetActiveFunctions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Získá pole instancí COR_ACTIVE_FUNCTION, které obsahují data o aktivních funkcích v rámečcích vlákna.|  
|[GetConnectionID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Získá identifikátor připojení pro tento `ICorDebugThread2`.|  
|[GetTaskID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Získá identifikátor úkolu pro tento `ICorDebugThread2`.|  
|[GetVolatileOSThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Získá identifikátor vlákna operačního systému pro tento `ICorDebugThread2`.|  
|[InterceptCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Umožňuje ladicímu programu zachytit aktuální výjimku ve vlákně.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
