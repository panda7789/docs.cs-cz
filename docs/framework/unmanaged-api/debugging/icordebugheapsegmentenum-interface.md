---
title: "ICorDebugHeapSegmentEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b477631b5920401127d34b2304485bd32c3d78f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
