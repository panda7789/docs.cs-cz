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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f2177702c6c5999033d0852a932e52c0725fb8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422656"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles – metoda
Získá enumerátor pro objekt popisovače v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `types`  
 [v] Bitovou kombinaci [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnoty, které určuje typ obslužné rutiny, které chcete zahrnout do kolekce.  
  
 `ppENum`  
 [out] Ukazatel na adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) tedy enumerátor pro objekty být uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateHandles` je pomocné funkce, která podporuje kontroly tabulky popisovače. Je podobná [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metoda, vyjma toho, že místo naplnění [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekce se všemi objekty být uklizeny, ho obsahuje pouze objekty, které mají obslužné rutiny z tabulky popisovače.  
  
 `types` Parametr určuje typy popisovač pro zahrnutí do kolekce. `types` může být libovolná z následujících tří členů [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) výčtu:  
  
-   `CorHandleStrongOnly` (zpracovává jenom silné odkazů na).  
  
-   `CorHandleWeakOnly` (zpracovává jenom slabé odkazy).  
  
-   `CorHandleAll` (všechny obslužné rutiny).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
