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
ms.openlocfilehash: 4a65a98ee04c3870dae2f49b3da2a8e72b1ffae4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795827"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType – výčet
Určuje typ rámce zásobníku. Tento výčet používá metoda [ICorDebugInternalFrame:: getframetype –](icordebuginternalframe-getframetype-method.md) .  
  
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
|`STUBFRAME_NONE`|Hodnota null. `ICorDebugInternalFrame::GetFrameType` Metoda nikdy tuto hodnotu nevrátí.|  
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
