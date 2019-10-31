---
title: ICorDebugManagedCallback::DebuggerError – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137376"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError – metoda
Oznamuje ladicímu programu, že došlo k chybě při pokusu o zpracování události ze společného jazykového modulu runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.  
  
 `errorHR`  
 pro Hodnota HRESULT, která byla vrácena z obslužné rutiny události.  
  
 `errorCode`  
 pro Celé číslo, které určuje chybu CLR.  
  
## <a name="remarks"></a>Poznámky  
 Tento proces může být umístěn do předávacího režimu v závislosti na povaze chyby.  
  
 `DebugError` zpětné volání indikuje, že služby ladění byly kvůli chybě zakázané, takže ladicí program by měl uživatelům zpřístupnit chybovou zprávu. [ICorDebugProcess:: getId –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) bude bezpečné volat, ale žádné jiné metody, včetně [ICorDebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměly být volány. Ladicí program by měl pro ukončení procesů používat zařízení s operačním systémem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
