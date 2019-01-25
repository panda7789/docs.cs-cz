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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2296f6e386f35aed91a8aea4392a9cd00ec27ccb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724356"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState – výčet
Určuje stav vlákna pro ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`THREAD_RUN`|Vlákno se spustí bez omezení, pokud dojde k události ladění.|  
|`THREAD_SUSPEND`|Vlákno nelze spustit.|  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program používá `CorDebugThreadState` výčet k řízení provádění vlákna. Stav vlákna lze nastavit pomocí [icordebugthread::setdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) nebo [icordebugcontroller::setallthreadsdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metody.  
  
 Zpětné volání k dispozici na [hostování API](../../../../docs/framework/unmanaged-api/hosting/index.md) umožňuje – čerpání zpráv, takže není potřeba přerušené stavu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDegug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
