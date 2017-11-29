---
title: "ICorDebugProcess5::EnumerateHandles – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5377f4ce0571cdb1de6c338f4bbb87d6a589aaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 `EnumerateHandles`je pomocné funkce, která podporuje kontroly tabulky popisovače. Je podobná [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metoda, vyjma toho, že místo naplnění [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekce se všemi objekty být uklizeny, ho obsahuje pouze objekty, které mají obslužné rutiny z tabulky popisovače.  
  
 `types` Parametr určuje typy popisovač pro zahrnutí do kolekce. `types`může být libovolná z následujících tří členů [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) výčtu:  
  
-   `CorHandleStrongOnly`(zpracovává jenom silné odkazů na).  
  
-   `CorHandleWeakOnly`(zpracovává jenom slabé odkazy).  
  
-   `CorHandleAll`(všechny obslužné rutiny).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
