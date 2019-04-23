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
ms.openlocfilehash: 54652727b4684d71068a19eb5eeb2e862f413f25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215076"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason – výčet
Určuje důvody, proč může zablokování vlákna na daný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`BLOCKING_NONE`|Pouze pro interní použití.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Vlákno se pokouší získat kritický oddíl, který je přidružený k uzamčení monitoru objektu. Obvykle to nastane, pokud voláním <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody.|  
|`BLOCKING_MONITOR_EVENT`|Vlákno čeká na událost, která je přidružený k uzamčení monitoru objektu. Obvykle to nastane, pokud voláním <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metody.|  
  
## <a name="remarks"></a>Poznámky  
 Při `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` člena se používá v [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury, `pBlockingObject` členem struktury odkazuje na rozhraní "ICorDebugValue", který představuje objekt, který je zadání . Je také zaručeno, že k implementaci [icordebugheapvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
