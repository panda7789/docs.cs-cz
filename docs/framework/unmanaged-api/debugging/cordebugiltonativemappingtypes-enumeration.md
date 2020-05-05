---
title: CorDebugIlToNativeMappingTypes – výčet
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795843"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a>CorDebugIlToNativeMappingTypes – výčet
Označuje, zda určitý rozsah nativních instrukcí, reprezentovaných instancí COR_DEBUG_IL_TO_NATIVE_MAP struktury, odpovídá zvláštní oblasti kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`NO_MAPPING`|Rozsah nativních instrukcí neodpovídá žádné zvláštní oblasti kódu.|  
|`PROLOG`|Rozsah nativních instrukcí odpovídá prologu.|  
|`EPILOG`|Rozsah nativních instrukcí odpovídá epilogu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetILToNativeMapping – metoda](icordebugcode-getiltonativemapping-method.md)
- [Ladění výčtů](debugging-enumerations.md)
