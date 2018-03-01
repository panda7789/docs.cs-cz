---
title: "COR_HEAPINFO – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 991e018c3967693f5b87b71c77cdbadcd4ae0cfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corheapinfo-structure"></a>COR_HEAPINFO – struktura
Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je vyčíslitelná.  
  
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
|`areGCStructuresValid`|`true`Pokud jsou platné struktury kolekce paměti a mohou být uvedené halda; v opačném `false`.|  
|`pointerSize`|Velikost v bajtech, ukazatelů na cílové architektury.|  
|`numHeaps`|Počet logických uvolňování paměti haldách v procesu.|  
|`concurrent`|`TRUE`Pokud je to souběžné uvolňování paměti (pozadí) je povoleno; v opačném `FALSE`.|  
|`gcType`|Člen [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) výčtu, která určuje, zda má systém uvolňování běží na pracovní stanici nebo na serveru.|  
  
## <a name="remarks"></a>Poznámky  
 Instance `COR_HEAPINFO` struktura vrátí volání [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda.  
  
 Před vytváření výčtu objektů v haldě kolekce paměti, je nutné vždy zkontrolovat `areGCStructuresValid` pole zajistit, že halda je ve stavu vyčíslitelná. Další informace najdete v tématu [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
