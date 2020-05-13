---
title: ICorDebugManagedCallback::BreakpointSetError – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: 0fa25dd33223ad2a9521aed0917ce35a2a33fa2f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213384"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError – metoda
Oznamuje ladicímu programu, že modul CLR (Common Language Runtime) nedokázal přesně navazovat zarážku, která byla nastavena předtím, než byla funkce kompilována za běhu (just-in-time).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující nevázanou zarážku.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje vlákno obsahující nevázanou zarážku.  
  
 `pBreakpoint`  
 pro Ukazatel na objekt ICorDebugBreakpoint, který představuje nevázanou zarážku.  
  
 `dwError`  
 pro Celé číslo, které označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 Tato zarážka nebude nikdy dosaženo. Ladicí program by měl ho deaktivovat a znovu vytvořit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
