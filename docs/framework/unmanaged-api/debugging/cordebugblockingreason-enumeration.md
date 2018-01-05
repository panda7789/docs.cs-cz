---
title: "CorDebugBlockingReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingReason
helpviewer_keywords: CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84c09de4e0ce6e436c2c814c4cd9990db012d422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason – výčet
Určuje z důvodů, proč může zablokování vlákna na daný objekt.  
  
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
|`BLOCKING_NONE`|Pouze interní použití.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Vlákno se pokouší získat důležité oddíl, který je přidružen monitorování zámek objektu. Obvykle k tomu dojde při volání jednoho z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody.|  
|`BLOCKING_MONITOR_EVENT`|Vlákno čeká na událost, která souvisí s monitorování zámek objektu. Obvykle k tomu dojde při volání jednoho z <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metody.|  
  
## <a name="remarks"></a>Poznámky  
 Když `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` člen se používá v [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktura, `pBlockingObject` člen struktura ukazuje na rozhraní "ICorDebugValue", který představuje objekt, který jste právě zadali . Je také zaručit implementovat [icordebugheapvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
