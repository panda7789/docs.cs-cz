---
title: ICorDebugProcess5::EnumerateHeap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 780f9eb0984e35c4487d770b5e7ff33917cf07ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792419"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap – metoda
Získá enumerátor pro objekty na spravované haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 mimo Ukazatel na adresu objektu rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) , který je enumerátorem pro objekty, které jsou umístěny na spravované haldě.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody `ICorDebugProcess5::EnumerateHeap` byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu pole `areGCStructuresValid` vráceného objektu [COR_HEAPINFO](cor-heapinfo-structure.md) , abyste zajistili, že halda uvolňování paměti v aktuálním stavu je vyčíslitelné. Kromě toho `ICorDebugProcess5::EnumerateHeap` vrátí `E_FAIL`, pokud se připojíte příliš brzy během životnosti procesu, než se přidělí paměť pro spravovanou haldu.  
  
 Objekt rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_HEAPOBJECT](cor-heapobject-structure.md) . Tato metoda naplní objekt kolekce [ICorDebugHeapEnum –](icordebugheapenum-interface.md) instancemi [COR_HEAPOBJECT](cor-heapobject-structure.md) , které poskytují informace o všech objektech. Kolekce může také zahrnovat [COR_HEAPOBJECT](cor-heapobject-structure.md) instance, které poskytují informace o objektech, které nejsou rootem žádného objektu, ale ještě nebyly shromážděny systémem uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
