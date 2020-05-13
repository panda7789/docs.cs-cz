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
ms.openlocfilehash: 50b0859d6727a25906f2c8b0f3fe96da228ab886
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213553"
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
 Před voláním `ICorDebugProcess5::EnumerateHeapRegions` metody byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu `areGCStructuresValid` pole vráceného objektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby se zajistilo, že halda uvolňování paměti v jejím aktuálním stavu je vyčíslitelné. Kromě toho `ICorDebugProcess5::EnumerateHeapRegions` Metoda vrátí, `E_FAIL` Pokud se připojíte příliš brzy během životnosti procesu, před vytvořením oblastí paměti.  
  
 Tato metoda zaručuje výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se spravované objekty skutečně nacházejí v těchto oblastech. Objekt kolekce [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) může zahrnovat prázdné nebo rezervované oblasti paměti.  
  
 Objekt rozhraní [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_SEGMENT](cor-segment-structure.md) . Každý objekt [COR_SEGMENT](cor-segment-structure.md) poskytuje informace o rozsahu paměti konkrétního segmentu spolu s generováním objektů v tomto segmentu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
