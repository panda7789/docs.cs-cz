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
ms.openlocfilehash: 291b384d6f0c8c1404b380c653693ec65fcfc960
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213410"
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
 pro Bitová kombinace hodnot [CorGCReferenceType –](corgcreferencetype-enumeration.md) , která určuje typ popisovačů, které mají být zahrnuty do kolekce.  
  
 `ppENum`  
 mimo Ukazatel na adresu [ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md) , která je enumerátorem pro objekty, které mají být shromážděny z paměti.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateHandles`je pomocná funkce, která podporuje kontrolu tabulky popisovačů. Je podobný jako metoda [ICorDebugProcess5:: EnumerateGCReferences –](icordebugprocess5-enumerategcreferences-method.md) , s výjimkou toho, že místo naplnění kolekce [ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md) se všemi objekty, které mají být sbírány do paměti, zahrnuje pouze objekty, které mají popisovače z tabulky popisovačů.  
  
 `types`Parametr určuje typy popisovačů, které se mají zahrnout do kolekce. `types`může to být kterýkoli z následujících tří členů výčtu [CorGCReferenceType –](corgcreferencetype-enumeration.md) :  
  
- `CorHandleStrongOnly`(zpracovává pouze silné odkazy).  
  
- `CorHandleWeakOnly`(zpracovává pouze slabé odkazy).  
  
- `CorHandleAll`(všechny popisovače).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
