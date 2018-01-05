---
title: "ICorDebugManagedCallback::DebuggerError – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc92bc6a1718d9d3505443e5b13786d1a359481f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError – metoda
Upozorní ladicí program, že došlo k chybě při pokusu o zpracování události z common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProcess`  
 [v] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve které došlo k události.  
  
 `errorHR`  
 [v] Hodnota HRESULT, která byla vrácena z obslužné rutiny události.  
  
 `errorCode`  
 [v] Celé číslo, které určuje chyba CLR.  
  
## <a name="remarks"></a>Poznámky  
 Proces může být zařazen do průchozí režimu, v závislosti na povaze chyby.  
  
 `DebugError` Zpětného volání označuje, že ladění služby byly zakázány kvůli chybě, takže ladicí programy měli chybová zpráva k dispozici pro uživatele. [Icordebugprocess::getid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) bude bezpečné volání, ale všechny ostatní způsoby, včetně [icordebug::Terminate –](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměl být volán. Ladicí program měli použít zařízení pro operační systém pro ukončení procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
