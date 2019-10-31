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
ms.openlocfilehash: 3ab4da3fcf43731587dae6f3a8e82ea48c5ee1ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129633"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions – metoda
Získá enumerátor pro rozsahy paměti spravované haldy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRegions`  
 mimo Ukazatel na adresu objektu rozhraní [ICorDebugHeapSegmentEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) , který je enumerátorem pro rozsahy paměti, ve které se objekty nacházejí ve spravované haldě.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody `ICorDebugProcess5::EnumerateHeapRegions` byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu pole `areGCStructuresValid` vráceného objektu [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , aby se zajistilo, že halda uvolňování paměti v jeho aktuální stav je vyčíslitelné. Kromě toho metoda `ICorDebugProcess5::EnumerateHeapRegions` vrátí `E_FAIL`, pokud se připojíte příliš brzy během životnosti procesu, před vytvořením oblastí paměti.  
  
 Tato metoda zaručuje výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se spravované objekty skutečně nacházejí v těchto oblastech. Objekt kolekce [ICorDebugHeapSegmentEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) může zahrnovat prázdné nebo rezervované oblasti paměti.  
  
 Objekt rozhraní [ICorDebugHeapSegmentEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) . Každý objekt [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) poskytuje informace o rozsahu paměti konkrétního segmentu spolu s generováním objektů v tomto segmentu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
