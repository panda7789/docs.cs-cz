---
title: ICorDebugHeapEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138492"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum – rozhraní
Poskytuje enumerátor pro objekty na spravované haldě. Toto rozhraní je podtřídou rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|Získá zadaný počet instancí [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které obsahují informace o objektech na spravované haldě.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugHeapEnum` implementuje rozhraní ICorDebugEnum.  
  
 Instance `ICorDebugHeapEnum` se naplní instancemi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním metody [ICorDebugProcess5:: EnumerateHeap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) . Každá instance [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) v kolekci představuje buď živý objekt na haldě, nebo objekt, který není rootem žádného objektu, ale ještě nebyl shromážděn systémem uvolňování paměti. Objekty [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) v kolekci lze vyčíslit voláním metody [ICorDebugHeapEnum –:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
