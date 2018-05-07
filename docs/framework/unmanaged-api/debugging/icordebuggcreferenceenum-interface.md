---
title: ICorDebugGCReferenceEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa8c3160dc779b2475dec63be896af5283cf5346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum – rozhraní
Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které budou uvolňování paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugGCReferenceEnum` Rozhraní implementuje rozhraní "ICorDebugEnum".  
  
 `ICorDebugGCReferenceEnum` Se zobrazí v instanci [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instance voláním [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metoda. [Cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty mohou být uvedené voláním [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) metoda.  
  
 [Cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objektů v kolekcích naplněno touto metodou představují tři typy objektů:  
  
-   Objekty z všechny spravované zásobníky. To zahrnuje za provozu odkazy ve spravovaném kódu a také objekty vytvořené modul common language runtime.  
  
-   Objekty z tabulky popisovače. To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.  
  
-   Objekty z fronty finalizační metodu. Fronty finalizační metodu kořeny objekty, dokud finalizační metodu byla spuštěna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
