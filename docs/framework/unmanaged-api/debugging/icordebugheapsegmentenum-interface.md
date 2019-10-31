---
title: ICorDebugHeapSegmentEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138452"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum – rozhraní
Poskytuje enumerátor pro oblasti paměti spravované haldy. Toto rozhraní je podtřídou rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Získá zadaný počet instancí [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které obsahují informace o oblastech spravované haldy.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugHeapSegmentEnum` implementuje rozhraní ICorDebugEnum.  
  
 Instance `ICorDebugHeapSegmentEnum` se naplní instancemi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním metody [ICorDebugProcess5:: EnumerateHeapRegions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) . Objekty [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) v kolekci lze vyčíslit voláním metody [ICorDebugHeapSegmentEnum –:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) .  
  
 Objekt `ICorDebugHeapSegmentEnum` Collection vypíše všechny oblasti paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se v těchto oblastech skutečně nacházejí spravované objekty. Může obsahovat informace o prázdných nebo rezervovaných oblastech paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
