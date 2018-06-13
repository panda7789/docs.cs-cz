---
title: CorDebugIntercept – výčet
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ee2272a43d9f71cd49754a7f4233868b8bb9134
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406589"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
