---
title: CorDebugThreadState – výčet
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133695"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState – výčet
Určuje stav vlákna pro ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`THREAD_RUN`|Vlákno funguje volně, pokud nedojde k události ladění.|  
|`THREAD_SUSPEND`|Vlákno nelze spustit.|  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program používá výčet `CorDebugThreadState` k řízení provádění vlákna. Stav vlákna lze nastavit pomocí metody [ICorDebugThread:: SetDebugState –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) nebo [ICorDebugController:: SetAllThreadsDebugState –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) .  
  
 Zpětné volání, které je poskytované [hostujícímu rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md) , povoluje pumpování zpráv, takže stav přerušeno není potřeba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
