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
ms.openlocfilehash: bd1e86b83c43af20604416f158ab9e74f399821b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894968"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue – rozhraní

Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo multidimenzionální pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBaseIndicies – metoda](icordebugarrayvalue-getbaseindicies-method.md)|Získá základní index každé dimenze v poli.|  
|[GetCount – metoda](icordebugarrayvalue-getcount-method.md)|Získá celkový počet prvků v poli.|  
|[GetDimensions – metoda](icordebugarrayvalue-getdimensions-method.md)|Získá rozměry pole.|  
|[GetElement – metoda](icordebugarrayvalue-getelement-method.md)|Získá hodnotu reprezentující daný prvek v poli.|  
|[GetElementAtPosition – metoda](icordebugarrayvalue-getelementatposition-method.md)|Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.|  
|[GetElementType – metoda](icordebugarrayvalue-getelementtype-method.md)|Získá jednoduchý typ prvků v poli.|  
|[GetRank – metoda](icordebugarrayvalue-getrank-method.md)|Získá počet rozměrů v poli.|  
|[HasBaseIndicies – metoda](icordebugarrayvalue-hasbaseindicies-method.md)|Určuje, zda pole obsahuje základní indexy.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugArrayValue`podporuje jak jednorozměrná, tak multidimenzionální pole.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
