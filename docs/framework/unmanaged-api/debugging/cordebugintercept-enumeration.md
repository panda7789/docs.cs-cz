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
ms.openlocfilehash: 144bdb1b4e479c1e75f89911ad5002e2650e405d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098113"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept – výčet
Určuje typy kódu, které mohou být zachyceny (to je od-steped do).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`INTERCEPT_NONE`|Nelze zachytit žádný kód.|  
|`INTERCEPT_CLASS_INIT`|Může být zachycen konstruktor.|  
|`INTERCEPT_EXCEPTION_FILTER`|Je možné zachytit filtr výjimky.|  
|`INTERCEPT_SECURITY`|Kód, který vynutil zabezpečení, lze zachytit.|  
|`INTERCEPT_CONTEXT_POLICY`|Můžete zachytit zásady kontextu.|  
|`INTERCEPT_INTERCEPTION`|Nepoužívá se.|  
|`INTERCEPT_ALL`|Veškerý kód může být zachycen.|  
  
## <a name="remarks"></a>Poznámky  
 Použijte metodu [ICorDebugStepper:: SetInterceptMask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) pro vytvoření typů kódu, který lze zachytit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
