---
title: ICorDebugProcess5::EnumerateGCReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0845165e3200d7a5e14715cbe116ea5255aa021
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948769"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences – metoda
Získá enumerátor pro všechny objekty, které mají být prováděno uvolnění paměti v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enumerateWeakReferences`  
 [in] Logická hodnota, která určuje, zda slabé odkazy taky jsou pro provedení výčtu. Pokud `enumerateWeakReferences` je `true`, `ppEnum` enumerátor obsahuje odkazy na silné a slabé odkazy. Pokud `enumerateWeakReferences` je `false`, enumerátor obsahuje pouze silné odkazy.  
  
 `ppEnum`  
 [out] Ukazatel na adresu [icordebuggcreferenceenum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , který je enumerátor pro objekty být uvolněna.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje způsob, jak určit úplný řetěz kořenové pro každý spravovaný objekt v procesu a je možné zjistit, proč je objekt stále aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
