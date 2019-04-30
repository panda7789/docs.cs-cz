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
ms.openlocfilehash: c2fecc7160cb41e31bf88f1a461265ad8fdce166
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792701"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult – výčet
Poskytuje podrobnosti o způsobu získání hodnoty ukazatel instrukce (IP).  
  
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
|`MAPPING_PROLOG`|Nativní kód je v prologu, takže IP má hodnotu 0.|  
|`MAPPING_EPILOG`|Nativní kód epilogu, probíhá, tedy hodnota IP adresu poslední instrukce metody.|  
|`MAPPING_NO_INFO`|Žádné informace o mapování je k dispozici pro metodu, aby IP adresa má hodnotu 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Přestože jsou informace o mapování metody, aktuální adresu nelze mapovat na kód Microsoft intermediate language (MSIL). IP adresa hodnotu 0.|  
|`MAPPING_EXACT`|Metoda mapuje přesně na kód jazyka MSIL nebo byl interpretován rámce, tak hodnota IP adresy je přesné.|  
|`MAPPING_APPROXIMATE`|Metoda byl úspěšně namapován, ale hodnota IP adresa může být přibližné.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít [icordebugilframe::getip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodu k získání hodnoty ukazatele na instrukci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
