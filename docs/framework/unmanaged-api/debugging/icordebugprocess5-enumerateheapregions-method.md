---
title: ICorDebugProcess5::EnumerateHeapRegions – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9340977c55c54b9a4683115000293d1c98dfcf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767455"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions – metoda
Získá enumerátor pro oblasti paměti spravované haldy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRegions`  
 [out] Ukazatel na adresu [icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) rozhraní objektu, který je enumerátor pro oblasti paměti, ve kterém jsou umístěny objekty ve spravované haldě.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním `ICorDebugProcess5::EnumerateHeapRegions` metoda, měli byste zavolat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkoumat hodnoty `areGCStructuresValid` pole vráceného [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Ujistěte se, že haldě uvolňování paměti v jejím aktuálním stavu vyčíslitelný objekt. Kromě toho `ICorDebugProcess5::EnumerateHeapRegions` vrátí metoda `E_FAIL` Pokud připojíte příliš brzy v doba života procesu, před paměti oblastech budou vytvořeny.  
  
 Tato metoda je zaručeno, že se vytvořit výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že spravované objekty ve skutečnosti jsou umístěny v těchto oblastech. [Icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objektu kolekce může zahrnovat oblasti prázdný nebo vyhrazené paměti.  
  
 [Icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objektu rozhraní je standardní výčet odvozený od icordebugenum – rozhraní, která umožňuje vytvořit výčet [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekty. Každý [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekt poskytuje informace o rozsahu paměti konkrétního segmentu, spolu s generování objekty v daném segmentu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
