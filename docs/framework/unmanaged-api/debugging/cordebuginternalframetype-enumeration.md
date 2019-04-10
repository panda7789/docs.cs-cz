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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05184ceb3b32eb003951fff5cfdfbfb813992552
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216051"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType – výčet
Určuje typ rámce zásobníku. Tento výčet je používán [icordebuginternalframe::getframetype –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`STUBFRAME_NONE`|Hodnotu null. `ICorDebugInternalFrame::GetFrameType` Metoda nikdy vrátí tuto hodnotu.|  
|`STUBFRAME_M2U`|Snímek spravovaného do nespravovaného zástupné procedury.|  
|`STUBFRAME_U2M`|Se zakázaným inzerováním nespravovaného do spravovaného rámce.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Přechod mezi doménami aplikace.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Volání metody zjednodušené.|  
|`STUBFRAME_FUNC_EVAL`|Počáteční vyhodnocení funkce.|  
|`STUBFRAME_INTERNALCALL`|Vnitřní volání do modulu common language runtime.|  
|`STUBFRAME_CLASS_INIT`|Začátek inicializace třídy.|  
|`STUBFRAME_EXCEPTION`|Výjimka, která je vyvolána výjimka.|  
|`STUBFRAME_SECURITY`|Rámeček pro zabezpečení přístupu kódu.|  
|`STUBFRAME_JIT_COMPILATION`|Modul runtime je JIT kompilaci metody.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
