---
title: "CorDebugMappingResult – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 793158ef63a0de27786dc8bd9b306f10c228054e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
