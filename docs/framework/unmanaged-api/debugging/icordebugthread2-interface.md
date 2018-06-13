---
title: Icordebugthread2 – Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c348cf28a6330523d1a490c136a3214e37d13f4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423046"
---
# <a name="icordebugthread2-interface1"></a>Icordebugthread2 – Interface1
Slouží jako logické rozšíření rozhraní ICorDebugThread.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetActiveFunctions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Získá pole cor_active_function – instancí, které obsahují údaje o active funkcí v podprocesu rámce.|  
|[GetConnectionID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Získá identifikátor připojení pro tento `ICorDebugThread2`.|  
|[GetTaskID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Získá identifikátor úlohy pro tento `ICorDebugThread2`.|  
|[GetVolatileOSThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Získá identifikátor operační systém pro tento `ICorDebugThread2`.|  
|[InterceptCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Umožňuje debugger zachytávat aktuální výjimky na vlákno.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
