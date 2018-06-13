---
title: ICorDebugStackWalk::SetContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6025a31f26c635ac40dcc2e35e7017be1c81feba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423008"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext – metoda
Nastaví [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) aktuální kontext objektu, který má platný kontext pro vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flag`  
 [v] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) příznak, který určuje, zda kontext je z aktivního rámce v zásobníku nebo získat unwinding zásobníku v kontextu.  
  
 `contextSize`  
 [v] Přidělenou velikost `CONTEXT` vyrovnávací paměti.  
  
 `context`  
 [v] `CONTEXT` Vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk` Objektu kontext byl úspěšně nastaven.|  
|E_FAIL|`ICorDebugStackWalk` Kontext objektu nebyl nastaven.|  
|E_INVALIDARG|Kontext má hodnotu null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Vyrovnávací paměti kontextu je příliš malá.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda nezmění aktuální kontext vlákno.  
  
 Nastavení aktuální kontext ke kontextu neplatný může způsobit nepředvídatelné výsledky z walkera zásobníku.  
  
 Přesná bitové kopie tohoto kontextu můžete načíst okamžitě voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
