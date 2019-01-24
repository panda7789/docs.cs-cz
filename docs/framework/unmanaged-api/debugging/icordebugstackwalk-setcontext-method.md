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
ms.openlocfilehash: 22eae4d59cbd6eba14e5784526c33774300a8367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493713"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext – metoda
Nastaví [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) aktuální kontext objektu na platný kontext pro vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flag`  
 [in] A [cordebugsetcontextflag –](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) příznak, který označuje, zda je kontext z aktivní rámec v zásobníku nebo kontext získané odvíjení zásobníku.  
  
 `contextSize`  
 [in] Přidělená velikost `CONTEXT` vyrovnávací paměti.  
  
 `context`  
 [in] `CONTEXT` Vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk` Objektu kontext byl úspěšně nastaven.|  
|E_FAIL|`ICorDebugStackWalk` Kontext objektu nebyl nastaven.|  
|E_INVALIDARG|Kontext je null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Kontext vyrovnávací paměť je příliš malá.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda nezmění kontext aktuálního vlákna.  
  
 Nastavení aktuálního kontextu Neplatný kontext může způsobit nepředvídatelné výsledky z zásobníkem.  
  
 Přesná bitové kopie tohoto kontextu můžete načíst okamžitě voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
