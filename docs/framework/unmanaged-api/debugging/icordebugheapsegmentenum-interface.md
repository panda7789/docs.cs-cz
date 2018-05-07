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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac4ddc33bcaf07d615fd186a63d96b1f4f6464c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum – rozhraní
Poskytuje enumerátor pro oblasti paměti spravované haldy. Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o oblastech spravovaná halda.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugHeapSegmentEnum` Rozhraní implementuje rozhraní ICorDebugEnum.  
  
 `ICorDebugHeapSegmentEnum` Se zobrazí v instanci [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance voláním [icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metoda. [Cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním mohou být uvedené v kolekci objektů [icordebugheapsegmentenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metoda.  
  
 `ICorDebugHeapSegmentEnum` Objektu kolekce zobrazí všechny oblasti paměti, které mohou obsahovat spravovaných objektů, ale nezaručí, že spravované objekty skutečně nacházejí v těchto oblastech. Může zahrnovat informace o oblastech prázdná nebo vyhrazené paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
