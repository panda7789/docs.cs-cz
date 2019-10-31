---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged – metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: abaf2d0542e16f526ecbe369370c31c225808f1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139348"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget:: ContinueStatusChanged – metoda
Změní stav pokračování pro nedokončenou událost ladění v zadaném vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadId`  
 Identifikátor vlákna definovaného operačním systémem.  
  
 `continueStatus`  
 Hodnota [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která představuje nový požadovaný stav pokračování.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volá metodu `ContinueStatusChanged`, když volá metodu ICorDebug, která vyžaduje, aby byla aktuální událost ladění zpracována způsobem, který se může lišit od způsobu, jakým by byl normálně zpracován. Například pokud existuje nedokončená výjimka a ladicí program požaduje operaci, která by zrušila výjimku (například [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API se používá k vyžádání zrušení výjimky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
