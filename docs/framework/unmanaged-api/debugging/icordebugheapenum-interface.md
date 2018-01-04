---
title: "ICorDebugHeapEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum
helpviewer_keywords: ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e317cb24e0eeaeaa38833433791eb546ee3c0478
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum – rozhraní
Poskytuje enumerátor pro objekty na spravované haldě. Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech v haldě spravované.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugHeapEnum` Rozhraní implementuje rozhraní ICorDebugEnum.  
  
 `ICorDebugHeapEnum` Se zobrazí v instanci [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metoda. Každý [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance v kolekci reprezentuje buď objekt za provozu v haldě nebo objekt, který není root pomocí libovolného objektu, ale nebyla ještě zjištěna modulem garbage collector. [Cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním mohou být uvedené v kolekci objektů [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
