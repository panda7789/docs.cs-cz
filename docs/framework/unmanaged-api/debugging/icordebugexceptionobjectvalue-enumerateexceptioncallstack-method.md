---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db0e794953578fccd08428b730b3d7951e13bee3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074076"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a>ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda
Získá enumerátor pro zásobník volání, které jsou součástí objektu výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 ppCallStackEnum  
 [out] Ukazatel na adresu [icordebugexceptionobjectcallstackenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) rozhraní objektu, který je výčet trasování zásobníku objektu spravované výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je k dispozici žádné informace o zásobníku volání, metoda vrátí `S_OK`, a [icordebugexceptionobjectcallstackenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) je platným enumerátorem o délce 0. Pokud je metoda nelze načíst informace o trasování zásobníku, vrácená hodnota je `E_FAIL` a je vrácena žádná enumerátor.  
  
 [Icordebugexceptionobjectcallstackenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) je zodpovědná za dekódování dat trasování zásobníku z objektu `_stackTrace` pole objektu výjimky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugExceptionObjectValue – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
