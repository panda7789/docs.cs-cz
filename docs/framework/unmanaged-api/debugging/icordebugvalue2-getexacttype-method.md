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
ms.openlocfilehash: 03d701d0801c55b6e91600f0767a6d737e4915c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479945"
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType – metoda
Získá ukazatel rozhraní na objekt, který představuje "ICorDebugType" <xref:System.Type> z této hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje <xref:System.Type> hodnoty reprezentovaný tímto objektem "icordebugvalue2 –".  
  
## <a name="remarks"></a>Poznámky  
 Obecné typy podporující `GetExactType` metoda nahrazuje i [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metody, každý z které vrácené informace o typu hodnoty .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

