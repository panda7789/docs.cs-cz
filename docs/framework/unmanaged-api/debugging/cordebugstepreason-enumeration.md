---
title: CorDebugStepReason – výčet
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133679"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason – výčet
Označuje výsledek jednotlivého kroku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`STEP_NORMAL`|Krokování je normálně dokončeno v rámci stejné funkce.|  
|`STEP_RETURN`|Krokování se normálně dostálo po vrácení funkce.|  
|`STEP_CALL`|Krokování obvykle probíhá na začátku nově volané funkce.|  
|`STEP_EXCEPTION_FILTER`|Byla vygenerována výjimka a ovládací prvek byl předán filtru výjimky.|  
|`STEP_EXCEPTION_HANDLER`|Byla vygenerována výjimka a ovládací prvek byl předán obslužné rutině výjimky.|  
|`STEP_INTERCEPT`|Ovládací prvek byl předán do zachytávací.|  
|`STEP_EXIT`|Vlákno bylo ukončeno před dokončením kroku.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StepComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
