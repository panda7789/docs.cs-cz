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
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131815"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext – metoda
Nastaví aktuální kontext objektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) na platný kontext vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `flag`  
 pro Příznak [CorDebugSetContextFlag –](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) , který označuje, zda je kontext z aktivního rámce v zásobníku, nebo kontext získaný odvinutím zásobníku.  
  
 `contextSize`  
 pro Přidělená velikost vyrovnávací paměti `CONTEXT`.  
  
 `context`  
 pro Vyrovnávací paměť `CONTEXT`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Kontext objektu `ICorDebugStackWalk` byl úspěšně nastaven.|  
|E_FAIL|Kontext `ICorDebugStackWalk`ho objektu nebyl nastaven.|  
|E_INVALIDARG|Kontext má hodnotu null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Kontextová vyrovnávací paměť je příliš malá.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda nemění aktuální kontext vlákna.  
  
 Nastavení aktuálního kontextu na neplatný kontext může způsobit nepředvídatelné výsledky z Stack prohlížeč.  
  
 Přesnou bitovou kopii tohoto kontextu lze načíst ihned voláním metody [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
