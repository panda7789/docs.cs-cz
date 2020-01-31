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
ms.openlocfilehash: 9b96c0a2eca543b9e01ccf92b271b1aa7003c5c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781939"
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
  
 `DebugError` zpětné volání indikuje, že služby ladění byly kvůli chybě zakázané, takže ladicí program by měl uživatelům zpřístupnit chybovou zprávu. [ICorDebugProcess:: getId –](icordebugprocess-getid-method.md) bude bezpečné volat, ale žádné jiné metody, včetně [ICorDebug:: Terminate](icordebug-terminate-method.md), by neměly být volány. Ladicí program by měl pro ukončení procesů používat zařízení s operačním systémem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
