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
ms.openlocfilehash: 1953a3e0492e4cfcdaea761b68ea22cf5a4a8ed7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205523"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 – rozhraní
Rozšiřuje rozhraní ICorDebugProcess pro podporu přístupu ke spravované haldě, k poskytnutí informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z místní mezipaměti nativní bitové kopie aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnableNGenPolicy – metoda](icordebugprocess5-enablengenpolicy-method.md)|Nastaví hodnotu, která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.|  
|[EnumerateGCReferences – metoda](icordebugprocess5-enumerategcreferences-method.md)|Získá enumerátor pro všechny objekty, které mají být v procesu shromažďovány jako uvolňování paměti.|  
|[EnumerateHandles – metoda](icordebugprocess5-enumeratehandles-method.md)|Získá enumerátor pro popisovače objektů v procesu.|  
|[EnumerateHeap – metoda](icordebugprocess5-enumerateheap-method.md)|Získá enumerátor pro objekty na spravované haldě.|  
|[EnumerateHeapRegions – metoda](icordebugprocess5-enumerateheapregions-method.md)|Získá enumerátor pro oblasti spravované haldy.|  
|[GetArrayLayout – metoda](icordebugprocess5-getarraylayout-method.md)|Získá informace o rozložení pole v paměti.|  
|[GetGCHeapInformation – metoda](icordebugprocess5-getgcheapinformation-method.md)|Získá ukazatel na strukturu [COR_HEAPINFO](cor-heapinfo-structure.md) , která obsahuje informace o objektech, které mají být uvolňovány paměti na spravované haldě.|  
|[GetObject – metoda](icordebugprocess5-getobject-method.md)|Získá ukazatel na objekt na spravované haldě.|  
|[GetTypeFields – metoda](icordebugprocess5-gettypefields-method.md)|Získá ukazatel na pole, které obsahuje informace o poli pro typ založený na jeho identifikátoru typu.|  
|[GetTypeForTypeID – metoda](icordebugprocess5-gettypefortypeid-method.md)|Získá objekt typu, který poskytuje informace o objektu na základě jeho identifikátorů typu.|  
|[GetTypeID – metoda](icordebugprocess5-gettypeid-method.md)|Získá identifikátor typu objektu na zadané adrese.|  
|[GetTypeLayout – metoda](icordebugprocess5-gettypelayout-method.md)|Načte informace o rozložení objektu v paměti na základě jeho identifikátoru typu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní logicky rozšiřuje rozhraní ICorDebugProcess, ICorDebugProcess2 a [ICorDebugProcess3 –](icordebugprocess3-interface.md) .  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď z jiného počítače, nebo z jiného procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
