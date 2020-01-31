---
title: ICorDebugThread2::InterceptCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791455"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException – metoda
Umožňuje ladicímu programu zachytit aktuální výjimku v tomto vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrame`  
 pro Ukazatel na ICorDebugFrame, který představuje aktivní rámec zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Metodu `InterceptCurrentException` lze volat mezi zpětným voláním výjimky ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) nebo [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) a přidruženým voláním [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
