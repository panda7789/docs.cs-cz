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
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379836"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 – rozhraní
Slouží jako logické rozšíření rozhraní ICorDebugThread.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetActiveFunctions – metoda](icordebugthread2-getactivefunctions-method.md)|Získá pole instancí COR_ACTIVE_FUNCTION, které obsahují data o aktivních funkcích v rámečcích vlákna.|  
|[GetConnectionID – metoda](icordebugthread2-getconnectionid-method.md)|Získá identifikátor připojení `ICorDebugThread2` .|  
|[GetTaskID – metoda](icordebugthread2-gettaskid-method.md)|Načte identifikátor úkolu `ICorDebugThread2` .|  
|[GetVolatileOSThreadID – metoda](icordebugthread2-getvolatileosthreadid-method.md)|Získá identifikátor vlákna operačního systému `ICorDebugThread2` .|  
|[InterceptCurrentException – metoda](icordebugthread2-interceptcurrentexception-method.md)|Umožňuje ladicímu programu zachytit aktuální výjimku ve vlákně.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
