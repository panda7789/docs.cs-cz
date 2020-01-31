---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged – metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: c918bb60fba5bc1ec3f0f7c58b103d05a3c7ddfd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792864"
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
 Ladicí program volá metodu `ContinueStatusChanged`, když volá metodu ICorDebug, která vyžaduje, aby byla aktuální událost ladění zpracována způsobem, který se může lišit od způsobu, jakým by byl normálně zpracován. Například pokud existuje nedokončená výjimka a ladicí program požaduje operaci, která by zrušila výjimku (například [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API se používá k vyžádání zrušení výjimky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMutableDataTarget – rozhraní](icordebugmutabledatatarget-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
