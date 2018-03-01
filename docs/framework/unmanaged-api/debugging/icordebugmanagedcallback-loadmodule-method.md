---
title: "ICorDebugManagedCallback::LoadModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d17001db68043f5d46a90738a8ad3e0635de762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>ICorDebugManagedCallback::LoadModule – metoda
Upozorní ladicí program úspěšně načtena společný modul runtime (CLR) jazyk.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, do kterého se načetl modul.  
  
 `pModule`  
 [v] Ukazatel na ICorDebugModule objekt, který reprezentuje modulu CLR.  
  
## <a name="remarks"></a>Poznámky  
 `LoadModule` Zpětné volání poskytuje příslušnou dobu prozkoumat metadata pro modul, nastavte příznaky kompilátoru za běhu (JIT), nebo povolit nebo zakázat třídy načítání zpětných volání pro modul.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [UnloadModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
