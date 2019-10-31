---
title: CorDebugInternalFrameType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: e76800316885c27c697421d454341d5f0789c611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097955"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType – výčet
Určuje typ rámce zásobníku. Tento výčet používá metoda [ICorDebugInternalFrame:: getframetype –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`STUBFRAME_NONE`|Hodnota null. Metoda `ICorDebugInternalFrame::GetFrameType` nikdy tuto hodnotu nevrací.|  
|`STUBFRAME_M2U`|Nespravovaný rámeček se zástupnými procedurami spravovaného do nespravovaného kódu|  
|`STUBFRAME_U2M`|Nespravovaný rámec nespravovaného kódu.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Přechod mezi doménami aplikace.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Zjednodušené volání metody.|  
|`STUBFRAME_FUNC_EVAL`|Začátek vyhodnocení funkce.|  
|`STUBFRAME_INTERNALCALL`|Interní volání modulu CLR (Common Language Runtime).|  
|`STUBFRAME_CLASS_INIT`|Začátek inicializace třídy.|  
|`STUBFRAME_EXCEPTION`|Výjimka, která je vyvolána.|  
|`STUBFRAME_SECURITY`|Rámec používaný pro zabezpečení přístupu kódu.|  
|`STUBFRAME_JIT_COMPILATION`|Modul runtime je kompilace metody JIT.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
