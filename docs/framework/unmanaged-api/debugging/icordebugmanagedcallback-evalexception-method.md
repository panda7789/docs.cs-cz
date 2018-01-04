---
title: "ICorDebugManagedCallback::EvalException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EvalException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3aa26c9458796dd20af0e22dd4a9961225b59bfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackevalexception-method"></a>ICorDebugManagedCallback::EvalException – metoda
Upozorní ladicí program, že zkušební verzi ukončilo došlo k neošetřené výjimce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, ve kterém byla ukončena vyhodnocení.  
  
 `pThread`  
 [v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla ukončena vyhodnocení.  
  
 `pEval`  
 [v] Ukazatel na ICorDebugEval objekt, který představuje kód, který provádí vyhodnocení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
