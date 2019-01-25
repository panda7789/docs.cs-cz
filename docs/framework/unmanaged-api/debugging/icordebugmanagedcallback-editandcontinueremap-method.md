---
title: ICorDebugManagedCallback::EditAndContinueRemap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1e97b8df2ad81f91cd7250afbe4c5cc544ca6be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702246"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a>ICorDebugManagedCallback::EditAndContinueRemap – metoda
Tato metoda je zastaralá. Upozorní ladicího programu, že přemapování události odeslala do integrovaného vývojového prostředí (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 `EditAndContinueRemap` Metoda se volá, když byl pokus o spuštění kódu v původní verzi aktualizované funkce. Common language runtime zavolá `EditAndContinueRemap` metodu pro odeslání události přemapování do integrovaného vývojového prostředí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
