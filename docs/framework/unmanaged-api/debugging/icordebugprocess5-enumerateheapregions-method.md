---
title: "ICorDebugProcess5::EnumerateHeapRegions – metoda"
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
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 478a8490e57946a08670d9f86e1f6ebcc67703a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions – metoda
Získá enumerátor pro rozsahy spravovaná halda paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppRegions`  
 [out] Ukazatel na adresu [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) rozhraní objekt, který je enumerátor pro rozsahy, ve které objekty jsou umístěny v spravovaná halda paměti.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním `ICorDebugProcess5::EnumerateHeapRegions` metody by měly volat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkontrolujte hodnotu `areGCStructuresValid` pole vráceného objektu [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objekt, který chcete zkontrolujte, zda je vyčíslitelná kolekce halda paměti v jejím aktuálním stavu. Kromě toho `ICorDebugProcess5::EnumerateHeapRegions` metoda vrátí `E_FAIL` Pokud připojíte příliš brzy v doba platnosti procesu, před paměti oblasti budou vytvořeny.  
  
 Tato metoda záruku, že se vytvořit výčet všech oblastech paměti, které mohou obsahovat spravovaných objektů, ale nezaručí, že spravované objekty skutečně nacházejí v těchto oblastech. [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objektu kolekce může zahrnovat oblasti prázdná nebo vyhrazené paměti.  
  
 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objekt rozhraní je standardní enumerátor odvozen z rozhraní ICorDebugEnum, který umožňuje vytvořit výčet [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekty. Každý [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekt poskytuje informace o paměti rozsah určitý segment, společně s generování objektů v tomto segmentu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
