---
title: "COR_ACTIVE_FUNCTION – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ACTIVE_FUNCTION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ACTIVE_FUNCTION
helpviewer_keywords: COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7bb587f485427d9fd88e2f834d844ece18d336ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coractivefunction-structure"></a>COR_ACTIVE_FUNCTION – struktura
Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce. Tato struktura je používán [icordebugthread2::getactivefunctions –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pAppDomain`|Ukazatel na vlastníkem domény aplikace `ilOffset` pole.|  
|`pModule`|Ukazatel na modulu vlastníka `ilOffset` pole.|  
|`pFunction`|Ukazatel na funkci vlastník `ilOffset` pole.|  
|`ilOffset`|Posun Microsoft (MSIL intermediate language) rámečku.|  
|`flags`|Vyhrazeno pro budoucí rozšíření.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
