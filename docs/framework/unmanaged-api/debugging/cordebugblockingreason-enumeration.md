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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274133"
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
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Vlákno se snaží získat kritickou část, která je přidružena k zámku monitoru u objektu. Obvykle k tomu dochází při volání jedné z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> metod nebo. <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>|  
|`BLOCKING_MONITOR_EVENT`|Vlákno čeká na událost, která je přidružena k zámku monitoru pro objekt. Obvykle k tomu dochází při volání jedné z <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metod.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je člen `BLOCKING_MONITOR_EVENT` [](cordebugblockingobject-structure.md) `pBlockingObject` nebo použit ve struktuře CorDebugBlockingObject –, člen struktury odkazuje na rozhraní "ICorDebugValue", které představuje objekt, který je právě zadán. `BLOCKING_MONITOR_CRITICAL_SECTION` Je také zaručena implementace rozhraní [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [Ladění](index.md)
