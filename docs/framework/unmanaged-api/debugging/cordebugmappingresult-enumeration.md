---
title: CorDebugMappingResult – výčet
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 317dc2fe8403ae25949410423f1a28ad365caf6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789312"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult – výčet
Poskytuje podrobné informace o tom, jak byla získána hodnota ukazatele na instrukce (IP).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Nativní kód je v prologu, takže hodnota IP je 0.|  
|`MAPPING_EPILOG`|Nativní kód je ve epilogu, takže hodnota IP je adresa poslední instrukce metody.|  
|`MAPPING_NO_INFO`|Pro metodu nejsou k dispozici žádné informace o mapování, takže hodnota IP je 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|I když jsou pro metodu k dispozici informace o mapování, nemůže být aktuální adresa namapována na kód jazyka MSIL (Microsoft Intermediate Language). Hodnota IP je 0.|  
|`MAPPING_EXACT`|Buď je metoda mapována přesně na kód jazyka MSIL, nebo byl rámec interpretován, takže hodnota IP je přesná.|  
|`MAPPING_APPROXIMATE`|Metoda byla úspěšně namapována, ale hodnota IP adresy může být přibližná.|  
  
## <a name="remarks"></a>Poznámky  
 K získání hodnoty ukazatele na instrukci můžete použít metodu [ICorDebugILFrame:: getip –](icordebugilframe-getip-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
