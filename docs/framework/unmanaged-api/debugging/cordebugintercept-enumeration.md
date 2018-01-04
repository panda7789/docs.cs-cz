---
title: "CorDebugIntercept – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIntercept
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIntercept
helpviewer_keywords: CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 814ee1285780d5a3b02aa5926ad4628e339a9114
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept – výčet
Určuje typy kód, který mohou být zachyceny (které se do stupeň).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`INTERCEPT_NONE`|Mohou být zachyceny žádný kód.|  
|`INTERCEPT_CLASS_INIT`|Mohou být zachyceny konstruktor.|  
|`INTERCEPT_EXCEPTION_FILTER`|Mohou být zachyceny filtru výjimek.|  
|`INTERCEPT_SECURITY`|Kód, který vynucuje zabezpečení mohou být zachyceny.|  
|`INTERCEPT_CONTEXT_POLICY`|Mohou být zachyceny zásadu kontextu.|  
|`INTERCEPT_INTERCEPTION`|Nepoužívá se.|  
|`INTERCEPT_ALL`|Mohou být zachyceny veškerý kód.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [icordebugstepper::setinterceptmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metodu pro vytvoření typy kód, který může být zachycen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
