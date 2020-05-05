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
ms.openlocfilehash: 9c22ca47a606da0949529cf55655bbcde19cb5c9
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795661"
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
 Ladicí program používá `CorDebugThreadState` výčet k řízení provádění vlákna. Stav vlákna lze nastavit pomocí metody [ICorDebugThread:: SetDebugState –](icordebugthread-setdebugstate-method.md) nebo [ICorDebugController:: SetAllThreadsDebugState –](icordebugcontroller-setallthreadsdebugstate-method.md) .  
  
 Zpětné volání, které je poskytované [hostujícímu rozhraní API](../hosting/index.md) , povoluje pumpování zpráv, takže stav přerušeno není potřeba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
