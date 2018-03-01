---
title: "ICorDebugProcess5 – rozhraní"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e26f50967f0fb70e0593584e3f175d20a7b213e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 – rozhraní
Rozšiřuje rozhraní ICorDebugProcess podporující přístup k spravovaná halda k zadání informací o uvolňování paměti spravovaných objektů, a k určení, zda ladicí program načte bitové kopie z mezipaměti místní nativních bitových kopií aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnableNGenPolicy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Nastaví hodnotu, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.|  
|[EnumerateGCReferences – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Získá enumerátor pro všechny objekty, které mají být uklizeny v procesu.|  
|[EnumerateHandles – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Získá enumerátor pro objekt popisovače v procesu.|  
|[EnumerateHeap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Získá enumerátor pro objekty v haldě spravované.|  
|[EnumerateHeapRegions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Získá enumerátor pro oblasti spravovaná halda.|  
|[GetArrayLayout – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Získá informace o rozložení pole v paměti.|  
|[GetGCHeapInformation – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Získá odkazy [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) struktura, která obsahuje informace o objektech, které mají být uklizeny na spravované haldě.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Získá ukazatel na objekt spravovaná halda.|  
|[GetTypeFields – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Získá ukazatel na pole obsahující informace z pole pro typ podle jeho typ identifikátoru.|  
|[GetTypeForTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Získá typ objektu, která poskytuje informace o objektu na základě jeho typu identifikátory.|  
|[GetTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Získá typ identifikátor pro objekt na zadané adrese.|  
|[GetTypeLayout – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Získá informace o rozložení objektu v paměti podle jeho typ identifikátoru.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní logicky rozšiřuje ICorDebugProcess, icordebugprocess2 –, a [icordebugprocess3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) rozhraní.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně z jiného počítače nebo z jiného procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
