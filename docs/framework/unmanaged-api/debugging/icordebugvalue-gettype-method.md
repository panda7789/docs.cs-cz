---
title: ICorDebugValue::GetType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83265c4f6dffed76f1710378cf5293aac7020ef2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986890"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType – metoda
Získá základní typ tohoto objektu "ICorDebugValue".  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 [out] Ukazatel na hodnotu "Corelementtype –" výčtu, která určuje typ hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se objekt komplexního typu za běhu, tento typ se můžou zkoumat prostřednictvím odpovídající podtřídy třídy `ICorDebugValue` rozhraní. Například "ICorDebugObjectValue", která dědí z `ICorDebugValue`, představuje komplexního typu.  
  
 `GetType` a [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) každá z metod vrací informace o typu hodnoty. Jsou obě nahrazeny obecných typů podporujících [icordebugvalue2::getexacttype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
