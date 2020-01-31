---
title: CorDebugExceptionFlags – výčet
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: 6ef81e224f3573021ee96ac313ec4923928dedad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789401"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags – výčet
Poskytuje další informace o výjimce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Neexistuje žádná výjimka.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Výjimka je zachytila.<br /><br /> Načasování výjimky může být stále tak, aby ji ladicí program nemohl zachytit. Například pokud neexistuje žádný spravovaný kód pod aktuálním zpětným voláním nebo událost výjimky, která je výsledkem přílohy just-in-time (JIT), nelze výjimku zachytit.|  
  
## <a name="remarks"></a>Poznámky  
 Do tohoto výčtu lze přidat nové hodnoty v pozdějších verzích, proto byste měli připravit kód, který používá `CorDebugExceptionFlags` pro neočekávané hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
