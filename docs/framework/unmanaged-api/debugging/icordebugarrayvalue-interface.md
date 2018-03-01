---
title: ICorDebugArrayValue Interface1
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
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue Interface1
Podtřídou třídy icordebugheapvalue –, který představuje jednorozměrná nebo multidimenzionální pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBaseIndicies – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Získá základní index Každá dimenze v poli.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Získá celkový počet prvků v poli.|  
|[GetDimensions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Získá rozměry pole.|  
|[GetElement – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Získá hodnotu představující daného elementu v poli.|  
|[GetElementAtPosition – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Získá element na dané pozici, považuje pole jako pole jednorozměrná, počítáno od nuly.|  
|[GetElementType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Získá jednoduchý typ elementů v poli.|  
|[GetRank – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Získá počet dimenzí v poli.|  
|[HasBaseIndicies – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Určuje, zda pole má základní indexy.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugArrayValue`podporuje jednorozměrná i vícerozměrných polí.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
