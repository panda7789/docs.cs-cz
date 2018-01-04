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
ms.workload: dotnet
ms.openlocfilehash: 68c4f9452f8ccc9b4d48ee67755a311f32540247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [StepComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
