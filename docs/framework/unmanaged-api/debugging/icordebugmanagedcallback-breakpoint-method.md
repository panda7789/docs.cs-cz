---
title: ICorDebugManagedCallback::Breakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c13898443f27d7275a58823c8a94ec5657748f28
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477098"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a>ICorDebugManagedCallback::Breakpoint – metoda
Ladicí program upozorní, když zarážky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahuje zarážku.  
  
 `pThread`  
 [in] Ukazatel na objekt icordebugthread –, který představuje podproces, který obsahuje zarážku.  
  
 `pBreakpoint`  
 [in] Ukazatel na objekt ICorDebugBreakpoint představující zarážku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
