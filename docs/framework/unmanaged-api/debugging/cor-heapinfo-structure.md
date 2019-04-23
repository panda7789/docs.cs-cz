---
title: COR_HEAPINFO – struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23bda470b8b5812b567081ba268ad503ac39ecaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090352"
---
# <a name="corheapinfo-structure"></a>COR_HEAPINFO – struktura
Obsahuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, zda je vyčíslitelná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`areGCStructuresValid`|`true` Pokud se uvolňování paměti kolekce struktur jsou platné a jsou uvedené haldy; v opačném případě `false`.|  
|`pointerSize`|Velikost v bajtech, ukazatelů na cílové architektuře.|  
|`numHeaps`|Počet logických uvolňování paměti haldy v procesu.|  
|`concurrent`|`TRUE` Pokud souběžné uvolňování paměti (pozadí) je povoleno; v opačném případě `FALSE`.|  
|`gcType`|Člen [cordebuggctype –](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) výčet, který označuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.|  
  
## <a name="remarks"></a>Poznámky  
 Instance `COR_HEAPINFO` struktura je vrácený voláním [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.  
  
 Před vytváření výčtu objektů na haldě uvolňování paměti, musí vždy zkontrolujte `areGCStructuresValid` pole tak, aby byl haldy ve výčtu stavu. Další informace najdete v tématu [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
