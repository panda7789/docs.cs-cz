---
title: "CorDebugStepReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32892a14de820e8add38654cef92aa44930aec62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason – výčet
Určuje výsledek jednotlivé kroky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`STEP_NORMAL`|Krokování s dokončit za normálních okolností v rámci stejné funkce.|  
|`STEP_RETURN`|Krokování s dál za normálních okolností po funkce vrátila.|  
|`STEP_CALL`|Krokování s dál za normálních okolností na začátku nově volaná funkce.|  
|`STEP_EXCEPTION_FILTER`|Vygenerovalo výjimku a byla předána ovládací prvek filtru výjimek.|  
|`STEP_EXCEPTION_HANDLER`|Vygenerovalo výjimku a řízení byl předán obslužnou rutinu výjimky.|  
|`STEP_INTERCEPT`|Ovládací prvek byl předán interceptoru.|  
|`STEP_EXIT`|Vlákno byl ukončen před krok bylo dokončeno.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Stepcomplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
