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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25af2c8fa3e3d49b3c2832a69f14b2691585d775
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489845"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError – metoda
Upozorní ladicího programu, že došlo k chybě při pokusu o zpracování události z common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.  
  
 `errorHR`  
 [in] Hodnota HRESULT, která byla vrácena z obslužné rutiny události.  
  
 `errorCode`  
 [in] Celé číslo, které určuje chyba CLR.  
  
## <a name="remarks"></a>Poznámky  
 Proces můžete umístit do režimu průchodu, v závislosti na povaze chyby.  
  
 `DebugError` Zpětného volání znamená, že ladění služby z důvodu chyby, byly zakázány, ladicí programy musí zpřístupnit chybová zpráva pro uživatele. [Icordebugprocess::getid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) budou bezpečné i volání, ale všechny ostatní metody, včetně [icordebug::Terminate –](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměla být volána. Ladicí program používejte operačního systému zařízení ukončování procesů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
