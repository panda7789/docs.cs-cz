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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993938"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 – rozhraní
Slouží jako logické rozšíření pro icordebugthread – rozhraní  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetActiveFunctions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Získává pole cor_active_function – instance, které obsahují údaje o aktivní funkce v rámcích vlákna.|  
|[GetConnectionID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Získá identifikátor připojení pro tento `ICorDebugThread2`.|  
|[GetTaskID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Získá identifikátor úlohy pro tento `ICorDebugThread2`.|  
|[GetVolatileOSThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Získá identifikátor vlákna operačního systému pro tento `ICorDebugThread2`.|  
|[InterceptCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Umožňuje ladicího programu a zachytit aktuální výjimku ve vlákně.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
