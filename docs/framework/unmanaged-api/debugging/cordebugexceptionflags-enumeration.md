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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d963a478ee7ae42159a0eb8a4b41cf20ae663aa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405447"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags – výčet
Poskytuje další informace o výjimce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Neexistuje žádná výjimka.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Výjimkou je interceptable.<br /><br /> Načasování výjimky stále může být tak, aby ladicí program nemůže zachytit ho. Například pokud není žádný spravovaný kód pod aktuální zpětného volání nebo události výjimky je výsledkem přílohy za běhu (JIT), nelze výjimka zachycena.|  
  
## <a name="remarks"></a>Poznámky  
 Nové hodnoty mohou být přidány do tento výčet v novějších verzích, měli byste kód, který používá `CorDebugExceptionFlags` neočekávané hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
