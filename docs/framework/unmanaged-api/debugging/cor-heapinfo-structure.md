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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179313"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO – struktura
Obsahuje obecné informace o haldě uvolňování paměti, včetně toho, zda je početovatelný.  
  
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
|`areGCStructuresValid`|`true`pokud jsou platné struktury uvolňování paměti a haldy mohou být uvedeny; v `false`opačném případě .|  
|`pointerSize`|Velikost v bajtů ukazatelů na cílové architektury.|  
|`numHeaps`|Počet hromady logické uvolňování paměti v procesu.|  
|`concurrent`|`TRUE`pokud je povoleno souběžné uvolňování paměti (pozadí); v `FALSE`opačném případě .|  
|`gcType`|Člen výčtu [CorDebugGCType,](cordebuggctype-enumeration.md) který označuje, zda je systém uvolňování paměti spuštěn na pracovní stanici nebo na serveru.|  
  
## <a name="remarks"></a>Poznámky  
 Instance `COR_HEAPINFO` struktury je vrácena voláním metody [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)  
  
 Před výčet objektů na haldě uvolňování paměti, `areGCStructuresValid` musíte vždy zkontrolovat pole, aby zajistily, že haldy je ve stavu výčtu. Další informace naleznete v metodě [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [ladění](index.md)
