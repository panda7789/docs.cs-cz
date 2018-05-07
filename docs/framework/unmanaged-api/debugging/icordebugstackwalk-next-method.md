---
title: ICorDebugStackWalk::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 367c43dc08722288dc3b32b5133f7770ffc3a27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next – metoda
Přesune [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu na další snímek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Modul runtime úspěšně odděleny na další snímek (viz poznámky).|  
|E_FAIL|`ICorDebugStackWalk` Objekt nelze rozšířené.|  
|CORDBG_S_AT_END_OF_STACK|V důsledku této unwind byl dosažen konec zásobníku.|  
|CORDBG_E_PAST_END_OF_STACK|Ukazatel na rámec je již na konec zásobníku; Proto je přístupná žádné další snímky.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `Next` Metoda záloh `ICorDebugStackWalk` do volání rámečku objektu pouze v případě, že modul runtime můžete unwind aktuální snímek. Objekt, jinak hodnota přejde na další snímek, který je schopen unwind modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugStackWalk – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
