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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult – výčet
Poskytuje podrobnosti o tom, jak byla získána hodnota ukazatele instrukce (IP).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`MAPPING_PROLOG`|Nativní kód je v prologu, takže IP hodnotu 0.|  
|`MAPPING_EPILOG`|Nativní kód je v epilogu, takže hodnota IP adresa je adresa poslední pokyn metody.|  
|`MAPPING_NO_INFO`|Žádné informace o mapování není k dispozici v případě metody, takže IP hodnotu 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|I když je informace o mapování pro metodu, s aktuální adresou nelze mapovat na kód Microsoft (MSIL intermediate language). IP adresa hodnotu 0.|  
|`MAPPING_EXACT`|Buď metodu mapuje přesně MSIL kód, nebo byla interpretovat rámečku, tak hodnota IP je přesný.|  
|`MAPPING_APPROXIMATE`|Metoda byl úspěšně přiřazen, ale může být hodnota parametru IP přibližné.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít [icordebugilframe::getip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodu k získání hodnoty ukazatele instrukcí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
