---
title: ICorDebugProcess5 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a105ca8838820b62e81dae4c0149734339bed7a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620211"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 – rozhraní
Rozšiřuje icordebugprocess – rozhraní pro podporu přístupu ke spravované haldě, k poskytování informací o uvolnění paměti spravovaných objektů, a k určení, zda ladicí program načítá obrázky z mezipaměti nativní bitové kopie místní aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnableNGenPolicy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Nastaví hodnotu, která určuje, jak aplikace načítá nativních bitových kopií při spuštění v rámci spravovaného ladicího programu.|  
|[EnumerateGCReferences – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Získá enumerátor pro všechny objekty, které mají být prováděno uvolnění paměti v procesu.|  
|[EnumerateHandles – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Získá enumerátor pro objekt popisovače procesu.|  
|[EnumerateHeap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Získá enumerátor pro objekty na spravované haldě.|  
|[EnumerateHeapRegions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Získá enumerátor pro oblasti spravované haldy.|  
|[GetArrayLayout – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Získá informace o rozložení pole v paměti.|  
|[GetGCHeapInformation – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Získá ukazatel [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) strukturu, která obsahuje informace o objektech, které mají být prováděno uvolnění paměti na spravované haldě.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Získá ukazatel na objekt na spravované haldě.|  
|[GetTypeFields – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Získá ukazatel na pole, která obsahuje informace o typu založeného na jeho identifikátor typu.|  
|[GetTypeForTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Získá typ objektu, který poskytuje informace o objektu na základě jeho typu identifikátory.|  
|[GetTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Získá identifikátor typu pro objekt na zadané adrese.|  
|[GetTypeLayout – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Získá informace o rozložení objektu v paměti podle jeho identifikátor typu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní rozšiřuje logicky ICorDebugProcess icordebugprocess2 –, a [icordebugprocess3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) rozhraní.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, z jiného počítače nebo z jiného procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
