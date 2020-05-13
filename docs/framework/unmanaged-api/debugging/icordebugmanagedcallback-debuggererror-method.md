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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205274"
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
  
 `DebugError`Zpětné volání indikuje, že služby ladění byly kvůli chybě zakázané, takže ladicí program by měl uživatelům zpřístupnit chybovou zprávu. [ICorDebugProcess:: getId –](icordebugprocess-getid-method.md) bude bezpečné volat, ale žádné jiné metody, včetně [ICorDebug:: Terminate](icordebug-terminate-method.md), by neměly být volány. Ladicí program by měl pro ukončení procesů používat zařízení s operačním systémem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
