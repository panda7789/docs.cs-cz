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
ms.openlocfilehash: 23ad8882ad97e5ceaeb690dfae08a6be55b85f64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791855"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext – metoda
Nastaví aktuální kontext objektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) na platný kontext vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `flag`  
 pro Příznak [CorDebugSetContextFlag –](cordebugsetcontextflag-enumeration.md) , který označuje, zda je kontext z aktivního rámce v zásobníku, nebo kontext získaný odvinutím zásobníku.  
  
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
  
 Přesnou bitovou kopii tohoto kontextu lze načíst ihned voláním metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
