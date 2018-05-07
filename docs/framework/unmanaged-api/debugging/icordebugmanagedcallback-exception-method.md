---
title: ICorDebugManagedCallback::Exception – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6152c643395fe52a43424cab33f527d577b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackexception-method"></a>ICorDebugManagedCallback::Exception – metoda
Upozorní ladicí program, že byla vyvolána výjimka ze spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, ve kterém byla výjimka vydána.  
  
 `pThread`  
 [v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla výjimka vydána.  
  
 `unhandled`  
 [v] Pokud je tato hodnota `false`, výjimka nebyl dosud byla zpracovaná aplikace; jinak, výjimka neošetřených a proces ukončí.  
  
## <a name="remarks"></a>Poznámky  
 Konkrétní výjimky mohou být načteny z objektu přístup z více vláken.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
