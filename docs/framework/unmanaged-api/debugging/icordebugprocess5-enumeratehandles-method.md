---
title: ICorDebugProcess5::EnumerateHandles – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129679"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles – metoda
Získá enumerátor pro popisovače objektů v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `types`  
 pro Bitová kombinace hodnot [CorGCReferenceType –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) , která určuje typ popisovačů, které mají být zahrnuty do kolekce.  
  
 `ppENum`  
 mimo Ukazatel na adresu [ICorDebugGCReferenceEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , která je enumerátorem pro objekty, které mají být shromážděny z paměti.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateHandles` je pomocná funkce, která podporuje kontrolu tabulky popisovačů. Je podobný jako metoda [ICorDebugProcess5:: EnumerateGCReferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) , s výjimkou toho, že místo naplnění kolekce [ICorDebugGCReferenceEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) se všemi objekty, které mají být sbírány do paměti, zahrnují pouze objekty, které mají popisovače. Tabulka popisovačů.  
  
 Parametr `types` určuje typy popisovačů, které se mají zahrnout do kolekce. `types` může být kterýkoli z následujících tří členů výčtu [CorGCReferenceType –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) :  
  
- `CorHandleStrongOnly` (zpracovává pouze silné odkazy).  
  
- `CorHandleWeakOnly` (zpracovává pouze slabé odkazy).  
  
- `CorHandleAll` (všechny popisovače).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
