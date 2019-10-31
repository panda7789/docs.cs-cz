---
title: CorDebugBlockingReason – výčet
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: bc488e55bf64468eb62e2dc6eaedca62ebde3310
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098989"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason – výčet
Určuje důvody, proč se vlákno může v daném objektu zablokovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`BLOCKING_NONE`|Pouze interní použití.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Vlákno se snaží získat kritickou část, která je přidružena k zámku monitoru u objektu. K tomu obvykle dochází při volání jedné z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>ch metod.|  
|`BLOCKING_MONITOR_EVENT`|Vlákno čeká na událost, která je přidružena k zámku monitoru pro objekt. Obvykle k tomu dochází, když zavoláte jednu z <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` metod.|  
  
## <a name="remarks"></a>Poznámky  
 Když je člen `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` použit ve struktuře [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , odkazuje `pBlockingObject` člen struktury na rozhraní "ICorDebugValue", které představuje objekt, který je právě zadán. Je také zaručena implementace rozhraní [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [Ladění](index.md)
