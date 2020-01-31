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
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792395"
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
 mimo Ukazatel na adresu objektu rozhraní [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) , který je enumerátorem pro rozsahy paměti, ve které se objekty nacházejí ve spravované haldě.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody `ICorDebugProcess5::EnumerateHeapRegions` byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu pole `areGCStructuresValid` vráceného objektu [COR_HEAPINFO](cor-heapinfo-structure.md) , abyste zajistili, že halda uvolňování paměti v aktuálním stavu je vyčíslitelné. Kromě toho metoda `ICorDebugProcess5::EnumerateHeapRegions` vrátí `E_FAIL`, pokud se připojíte příliš brzy během životnosti procesu, před vytvořením oblastí paměti.  
  
 Tato metoda zaručuje výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se spravované objekty skutečně nacházejí v těchto oblastech. Objekt kolekce [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) může zahrnovat prázdné nebo rezervované oblasti paměti.  
  
 Objekt rozhraní [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_SEGMENT](cor-segment-structure.md) . Každý objekt [COR_SEGMENT](cor-segment-structure.md) poskytuje informace o rozsahu paměti konkrétního segmentu spolu s generováním objektů v tomto segmentu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
