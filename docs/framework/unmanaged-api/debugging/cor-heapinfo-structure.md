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
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274195"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO – struktura
Poskytuje obecné informace o haldě uvolňování paměti, včetně toho, zda je vyčíslitelné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`areGCStructuresValid`|`true`Pokud jsou struktury uvolňování paměti platné a lze vytvořit výčet haldy; v opačném případě. `false`|  
|`pointerSize`|Velikost ukazatelů v cílové architektuře v bajtech.|  
|`numHeaps`|Počet hald logických uvolňování paměti v procesu.|  
|`concurrent`|`TRUE`Pokud je povolené shromažďování paměti souběžného (na pozadí); v opačném případě. `FALSE`|  
|`gcType`|Člen výčtu [CorDebugGCType –](cordebuggctype-enumeration.md) , který označuje, zda je systém uvolňování paměti spuštěn na pracovní stanici nebo serveru.|  
  
## <a name="remarks"></a>Poznámky  
 Instance `COR_HEAPINFO` struktury je vrácena voláním metody [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) .  
  
 Před vytvořením výčtu objektů v haldě uvolňování paměti je vždy nutné zaškrtnout `areGCStructuresValid` pole, aby se zajistilo, že je halda ve výčtovém stavu. Další informace naleznete v tématu metoda [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
