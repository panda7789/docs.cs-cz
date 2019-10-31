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
ms.openlocfilehash: c8cfc9cdf6580a002f6ac15080012a9e8c63be20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129652"
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
 mimo Ukazatel na adresu objektu rozhraní [ICorDebugHeapEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) , který je enumerátorem pro objekty, které jsou umístěny na spravované haldě.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody `ICorDebugProcess5::EnumerateHeap` byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu pole `areGCStructuresValid` vráceného objektu [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , aby se zajistilo, že halda uvolňování paměti v jeho aktuální stav je vyčíslitelné. Kromě toho `ICorDebugProcess5::EnumerateHeap` vrátí `E_FAIL`, pokud se připojíte příliš brzy během životnosti procesu, než se přidělí paměť pro spravovanou haldu.  
  
 Objekt rozhraní [ICorDebugHeapEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) . Tato metoda naplní objekt kolekce [ICorDebugHeapEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) instancemi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které poskytují informace o všech objektech. Kolekce může také zahrnovat instance [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které poskytují informace o objektech, které nejsou rootem žádného objektu, ale ještě nebyly shromážděny systémem uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
