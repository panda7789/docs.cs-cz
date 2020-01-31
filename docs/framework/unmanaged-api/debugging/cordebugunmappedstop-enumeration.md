---
title: CorDebugUnmappedStop – výčet
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: 23e168b0f322a580917c3fcfcb767a7d4d4628f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793884"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop – výčet
Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`STOP_NONE`|Nezastaví žádný typ nemapovaného kódu.|  
|`STOP_PROLOG`|Zastavit v kódu prologu.|  
|`STOP_EPILOG`|Zastavit v kódu epilogu|  
|`STOP_NO_MAPPING_INFO`|Zastavit v kódu, který nemá žádné informace o mapování.|  
|`STOP_OTHER_UNMAPPED`|Zastavit v nemapovaném kódu, který se nevejde do prologu, epilogu, žádného mapování-informace nebo nespravované kategorie.|  
|`STOP_UNMANAGED`|Zastavit v nespravovaném kódu Tato hodnota je platná pouze při ladění vzájemné spolupráce.|  
|`STOP_ALL`|Zastavte všechny typy nemapovaného kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Použijte metodu [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) pro nastavení příznaků, které určují Nemapovaný kód, ve kterém se stepper zastaví.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
