---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged – metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213306"
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
 Hodnota [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) , která představuje nový požadovaný stav pokračování.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volá `ContinueStatusChanged` metodu při volání metody ICorDebug, která vyžaduje, aby byla aktuální událost ladění zpracována způsobem, který se může lišit od způsobu, jakým by byl normálně zpracován. Například pokud existuje nevyřízená výjimka a ladicí program požaduje operaci, která by zrušila výjimku (například [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) nebo `FuncEval` ), toto rozhraní API se používá k vyžádání zrušení výjimky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMutableDataTarget – rozhraní](icordebugmutabledatatarget-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
