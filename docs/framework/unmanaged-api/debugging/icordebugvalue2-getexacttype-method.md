---
title: ICorDebugValue2::GetExactType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1f8292a6964a6b25e228fcd07ab21a7ee5f5a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType – metoda
Získá ukazatele rozhraní pro objekt "ICorDebugType", který představuje <xref:System.Type> této hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje <xref:System.Type> hodnoty představuje tento objekt "icordebugvalue2 –".  
  
## <a name="remarks"></a>Poznámky  
 Obecné typy podporující `GetExactType` metoda nahrazuje i [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metody, každý z které návratový informace o typu hodnoty .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
