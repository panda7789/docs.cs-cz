---
title: ICorDebugArrayValue – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168386"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue – rozhraní

Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo vícedimenzionální pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBaseIndicies – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Získá základní index každé dimenze v poli.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Získá celkový počet prvků v poli.|  
|[GetDimensions – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Získá rozměry pole.|  
|[GetElement – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Získá hodnotu představující daný prvek v poli.|  
|[GetElementAtPosition – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Získá prvek na dané pozici, zpracuje pole jako pole s nulovým základem, jednorozměrné.|  
|[GetElementType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Získá jednoduchý typ prvků v poli.|  
|[GetRank – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Získá počet dimenzí v poli.|  
|[HasBaseIndicies – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Určuje, zda pole obsahuje základní indexy.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugArrayValue` podporuje jednorozměrné i vícedimenzionální pole.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
