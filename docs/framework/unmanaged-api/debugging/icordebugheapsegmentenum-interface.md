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
ms.openlocfilehash: 98e3351c9c86961d11b0985117259d0ff3b609ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794410"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum – rozhraní
Poskytuje enumerátor pro oblasti paměti spravované haldy. Toto rozhraní je podtřídou rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icordebugheapsegmentenum-next-method.md)|Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o oblastech spravované haldy.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugHeapSegmentEnum` implementuje rozhraní ICorDebugEnum.  
  
 Instance `ICorDebugHeapSegmentEnum` se naplní pomocí [COR_HEAPOBJECT](cor-heapobject-structure.md) instancí voláním metody [ICorDebugProcess5:: EnumerateHeapRegions –](icordebugprocess5-enumerateheapregions-method.md) . Objekty [COR_HEAPOBJECT](cor-heapobject-structure.md) v kolekci lze vyčíslit voláním metody [ICorDebugHeapSegmentEnum –:: Next](icordebugheapsegmentenum-next-method.md) .  
  
 Objekt `ICorDebugHeapSegmentEnum` Collection vypíše všechny oblasti paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se v těchto oblastech skutečně nacházejí spravované objekty. Může obsahovat informace o prázdných nebo rezervovaných oblastech paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
