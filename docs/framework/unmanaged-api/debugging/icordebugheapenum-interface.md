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
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794426"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum – rozhraní
Poskytuje enumerátor pro objekty na spravované haldě. Toto rozhraní je podtřídou rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icordebugheapenum-next-method.md)|Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o objektech na spravované haldě.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugHeapEnum` implementuje rozhraní ICorDebugEnum.  
  
 Instance `ICorDebugHeapEnum` se naplní pomocí [COR_HEAPOBJECT](cor-heapobject-structure.md) instancí voláním metody [ICorDebugProcess5:: EnumerateHeap –](icordebugprocess5-enumerateheap-method.md) . Každá instance [COR_HEAPOBJECT](cor-heapobject-structure.md) v kolekci představuje buď živý objekt na haldě, nebo objekt, který není rootem žádného objektu, ale ještě nebyl shromážděn systémem uvolňování paměti. Objekty [COR_HEAPOBJECT](cor-heapobject-structure.md) v kolekci lze vyčíslit voláním metody [ICorDebugHeapEnum –:: Next](icordebugheapenum-next-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
